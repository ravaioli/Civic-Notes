# Appendix: Φ‑Score Calculation

The Φ‑Score (Phi Score) is the core metric of civic health on CivicNotes. It transforms the complex dynamics of community engagement, sentiment, and government responsiveness into a simple, legible number (0–100) that anyone can understand at a glance. This appendix explains how the Φ‑Score is calculated, the weight of each component, and the data sources that feed into it.

---

## What the Φ‑Score Measures

The Φ‑Score answers the question: **How healthy is civic discourse and engagement in this context?**

It measures four dimensions of civic health:

| Dimension | What It Measures | Weight |
|-----------|------------------|--------|
| **Participation** | Volume of engagement relative to population | 30% |
| **Clarity** | Coherence of sentiment (signal vs. noise) | 25% |
| **Responsiveness** | Official acknowledgment and action | 30% |
| **Connections** | Network density and relationships | 15% |

These dimensions are grounded in the Solarpunk Mandala framework, particularly the concepts of **Visible Heart** (making civic health legible) and **Boundary Permeability Index** (measuring how open governance is to citizen input).

---

## Data Sources

The Φ‑Score draws on multiple data sources:

| Source | Used For |
|--------|----------|
| **CivicNotes** | Participation volume, intent tags, reply networks |
| **User profiles** | Verification status, neighborhood, guild memberships |
| **Promise Tracker** | Promise statuses, verification rates, response times |
| **Petitions** | Signature counts, verification methods |
| **Guild activity** | Endorsements, proposal submissions |
| **Official responses** | Acknowledgments, addressed promises |
| **Geographic data** | District boundaries, population (for normalization) |

---

## Calculation Overview

The Φ‑Score is calculated as a weighted sum of four sub‑scores, each normalized to a 0–100 scale.
```markdown
Φ = (P × 0.30) + (C × 0.25) + (R × 0.30) + (N × 0.15)
```

Where:
- **P** = Participation score (0–100)
- **C** = Clarity score (0–100)
- **R** = Responsiveness score (0–100)
- **N** = Connections score (0–100)

Each sub‑score is calculated independently based on the context (agenda item, district, guild, etc.).

---

## Participation Score (P)

**Purpose:** Measures how many people are engaging, normalized for population.

### Formula
```markdown
P = min(100, (V × 100 / V_target) × 0.5 + (U × 100 / U_target) × 0.5)
```

Where:
- **V** = Volume of CivicNotes in the period
- **V_target** = Expected note volume based on historical baseline (e.g., 5% of population per month)
- **U** = Unique users who left notes
- **U_target** = Expected unique users (e.g., 3% of population)

### Factors

| Factor | Description |
|--------|-------------|
| **Raw note count** | Total CivicNotes on the item/in district |
| **Unique participants** | Number of distinct users |
| **Population normalization** | Adjusted for district population |
| **Time window** | Typically 30 days rolling |

### Example

District with 10,000 residents:
- V_target = 500 notes/month (5% of population)
- U_target = 300 users/month (3% of population)

Actual:
- V = 600 notes
- U = 250 users

Calculation:
- Note volume component = (600 / 500) × 50 = 60
- User count component = (250 / 300) × 50 = 41.7
- P = 60 + 41.7 = **101.7** → capped at 100

---

## Clarity Score (C)

**Purpose:** Measures whether discourse is coherent (clear consensus or well‑articulated diverse views) versus chaotic (noise, trolling, fragmentation).

### Formula
```markdown
C = (S × 0.4) + (T × 0.3) + (F × 0.3)
```

Where:
- **S** = Sentiment coherence score
- **T** = Topic coherence score
- **F** = Fragmentation penalty

### Sentiment Coherence (S)

Measures whether notes cluster around clear positions or are scattered.
```markdown
S = 100 × (1 - (H_observed / H_max))
```

Where:
- **H_observed** = Shannon entropy of intent tag distribution
- **H_max** = Maximum possible entropy (all five intents equally distributed)

Lower entropy (more concentrated in one or two intents) yields higher score.

**Example:**
- 80% Support, 10% Oppose, 10% Question: low entropy → high S
- 20% each across five intents: maximum entropy → low S

### Topic Coherence (T)

Measures whether notes focus on the actual agenda item versus tangential topics.

Derived from:
- Keyword matching between note text and item description
- Human‑flagged "off‑topic" notes (via community flagging)
- Reply threading relevance
```markdown
T = 100 × (relevant_notes / total_notes)
```

### Fragmentation Penalty (F)

Penalizes discourse that is highly fractured (many short threads, no engagement between opposing views).
```markdown
F = 100 × (1 - (isolated_notes / total_notes) × 0.5)
```

Where **isolated_notes** are notes with zero replies.

---

## Responsiveness Score (R)

**Purpose:** Measures how well officials acknowledge and act on citizen input. This is the most direct measure of boundary permeability.

### Formula
```markdown
R = (A_weighted × 0.4) + (D_weighted × 0.4) + (T_response × 0.2)
```

Where:
- **A_weighted** = Acknowledgment rate (weighted by promise verification)
- **D_weighted** = Addressed rate (weighted by promise verification)
- **T_response** = Response time score

### Acknowledgment Rate
```markdown
A_base = promises_acknowledged / promises_verified
A_weighted = A_base × (1 + 0.1 × log(guild_endorsements + 1))
```

Promises with guild endorsements count slightly more, reflecting broader community validation.

### Addressed Rate
```markdown
D_base = promises_addressed / promises_verified
D_weighted = D_base × (1 + 0.1 × log(guild_endorsements + 1))
```

### Response Time Score
```markdown
T_response = max(0, 100 - (avg_response_days × 2))
```

Capped at 0 for >50 days average response.

**Example:**
- Average response time = 12 days
- T_response = 100 - (12 × 2) = 76

### Special Cases

- If no promises exist in period, R defaults to **50** (neutral).
- For districts with no officials on platform, R is based on documented responses (from minutes, etc.).

---

## Connections Score (N)

**Purpose:** Measures the density and health of relationships among participants.

### Formula
```markdown
N = (G × 0.4) + (R_net × 0.3) + (X_boundary × 0.3)
```

Where:
- **G** = Guild participation score
- **R_net** = Reply network density
- **X_boundary** = Cross‑boundary engagement score

### Guild Participation (G)
```markdown
G = min(100, guild_members_engaged × 100 / guild_members_total + endorsed_notes × 2)
```

Measures:
- What percentage of guild members are active
- How many notes receive guild endorsements

### Reply Network Density (R_net)
```markdown

Measures:
- What percentage of guild members are active
- How many notes receive guild endorsements

### Reply Network Density (R_net)
```markdown
R_net = 100 × (actual_reply_edges / max_possible_edges)
```

Where:
- **actual_reply_edges** = Number of note–reply connections
- **max_possible_edges** = n(n-1)/2 where n = number of participants

Denser networks (more cross‑conversation) score higher.

### Cross‑Boundary Engagement (X_boundary)
```markdown
X_boundary = (cross_district_replies / total_replies) × 50 + (cross_guild_endorsements / total_endorsements) × 50
```

Measures engagement across:
- Different neighborhoods/districts
- Different guilds

High cross‑boundary engagement indicates a more integrated community.

---

## Putting It All Together: Example Calculation

### Context: Agenda Item "5th & Main Zoning"

| Metric | Value | Calculation |
|--------|-------|-------------|
| **Participation** | | |
| Notes | 45 | |
| Unique users | 32 | |
| Expected notes | 30 | Note component = (45/30)×50 = 75 |
| Expected users | 25 | User component = (32/25)×50 = 64 |
| | | **P = (75+64)/2 = 69.5** |

| **Clarity** | | |
| Sentiment entropy | 0.8 (H_max=2.32) | S = 100×(1-0.8/2.32) = 65.5 |
| Relevant notes | 38 of 45 | T = (38/45)×100 = 84.4 |
| Isolated notes | 12 | F = 100×(1-12/45×0.5) = 86.7 |
| | | **C = 65.5×0.4 + 84.4×0.3 + 86.7×0.3 = 77.9** |

| **Responsiveness** | | |
| Promises verified | 3 | |
| Acknowledged | 2 | A_base = 0.67 |
| Guild endorsements | 1 | A_weighted = 0.67×(1+0.1×log(2)) = 0.69 |
| Addressed | 1 | D_base = 0.33, D_weighted = 0.34 |
| Avg response days | 14 | T = 100-(14×2) = 72 |
| | | **R = 69×0.4 + 34×0.4 + 72×0.2 = 55.6** |

| **Connections** | | |
| Guild members engaged | 12 of 45 | G = (12/45)×100 + 3×2 = 32.7 |
| Reply edges | 28 of possible 496 | R_net = 28/496×100 = 5.6 |
| Cross‑district replies | 8 of 28 | X = (8/28)×50 + (2/5)×50 = 34.3 |
| Cross‑guild endorsements | 2 of 5 | |
| | | **N = 32.7×0.4 + 5.6×0.3 + 34.3×0.3 = 25.1** |

**Final Φ‑Score:**
```markdown
Φ = 69.5×0.30 + 77.9×0.25 + 55.6×0.30 + 25.1×0.15
= 20.85 + 19.48 + 16.68 + 3.77
= 60.78 ≈ 61
```

This agenda item has a Φ‑Score of **61** – in the "Stable/Stressed" range (41–70). Strong participation and clarity, but responsiveness and connections need improvement.

---

## Context‑Specific Adjustments

### For Districts

- Population normalization more important
- Responsiveness based on all promises to district officials
- Connections measured across neighborhood boundaries

### For Guilds

- Participation based on member activity, not population
- Responsiveness tracks how many guild‑endorsed items led to action
- Connections measures inter‑guild collaboration

### For Citywide View

- Aggregation of all district scores (weighted by population)
- Plus city‑wide metrics (cross‑district engagement, city‑wide petitions)

---

## Time Windows and Decay

The Φ‑Score uses a **rolling 30‑day window** for most metrics, with older data decaying:

- Days 1–30: Full weight
- Days 31–60: Half weight
- >60 days: Not included (except for long‑term trends)

This ensures the score reflects current civic health while smoothing short‑term fluctuations.

---

## Display and Interpretation

### Color Mapping

| Range | Color | Interpretation |
|-------|-------|----------------|
| **71–100** | Vibrant cyan to seafoam green | Thriving – healthy, engaged discourse |
| **41–70** | Gold to deep amber | Stable or stressed – active but with friction |
| **0–40** | Burnt orange to deep crimson | Fragile or critical – low engagement or high conflict |

### Sub‑Score Breakdown

When a user clicks on a Φ‑Score, they see:
```markdown
Φ 78
├─ Participation 82
├─ Clarity 85
├─ Responsiveness 74
└─ Connections 68
```

This helps users understand what's driving the overall score.

---

## Limitations and Caveats

| Limitation | Mitigation |
|------------|------------|
| **New communities** | Minimum data threshold (e.g., 10 notes) before Φ appears |
| **Small populations** | Scores may be volatile; displayed with confidence indicator |
| **Gaming attempts** | Fraud detection (duplicate accounts, coordinated voting) |
| **Off‑platform activity** | Only platform interactions counted |
| **Context matters** | Scores are comparative within similar contexts (agenda item vs. agenda item, not agenda vs. district) |

---

## Future Enhancements

| Enhancement | Description |
|-------------|-------------|
| **Sentiment analysis** | NLP to detect tone (respectful vs. hostile) |
| **Topic modeling** | Automatic detection of emergent themes |
| **Predictive scoring** | Forecast future Φ based on trends |
| **Individual contributions** | Show how each user affects Φ |
| **External data integration** | Incorporate offline engagement (attendance at meetings) |

---

## Technical Implementation

The Φ‑Score is calculated:

- **Daily** for districts and guilds
- **Real‑time** for agenda items (updates with each new note or promise)
- **On‑demand** for custom date ranges (in analytics)

A caching layer ensures performance while maintaining freshness.

---

## Why This Matters

The Φ‑Score transforms abstract civic dynamics into a tangible, actionable metric. It:

- **Makes the invisible visible** – Community health becomes legible.
- **Guides attention** – Users can see where engagement is needed.
- **Drives accountability** – Officials see their responsiveness scores.
- **Enables comparison** – Across districts, over time, against benchmarks.
- **Celebrates progress** – Rising scores show collective achievement.

In the Solarpunk Mandala framework, the Φ‑Score is a key expression of the **Visible Heart** – making the health of the civic body visible to all who participate in its care.

---

## Next Steps

- **[Core Concepts](../user-guide/core-concepts.md)** – Introduction to Φ‑Score for users.
- **[Promise Tracker](../user-guide/tracking-promises.md)** – How promises affect responsiveness.
- **[Analytics for Officials](../official-guide/dashboard-overview.md)** – How officials see and use Φ‑data.

The Φ‑Score is a living metric, refined continuously based on community feedback and emerging understanding of civic health.
