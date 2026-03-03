# UX Design Principles

The CivicNotes platform is more than a set of features—it's an expression of a philosophy. Every interaction, every visual element, and every flow is guided by a coherent set of design principles rooted in the Solarpunk Mandala and the vision of regenerative democracy. This document articulates those principles and explains how they shape the user experience.

---

## Why Design Principles Matter

Design principles serve as a compass. They help us:

- **Make consistent decisions** across features and platforms.
- **Evaluate tradeoffs** when different goals conflict.
- **Communicate intent** to designers, developers, and stakeholders.
- **Stay aligned with our values** even as the platform evolves.
- **Create coherence** so that CivicNotes feels like a unified whole, not a collection of parts.

---

## The Seven Pillars of CivicNotes Design
```markdown
┌─────────────────────────────────────────────────────────────┐
│ │
│ 1. Visible Heart · Make the invisible visible │
│ 2. Living System · Organic, not industrial │
│ 3. Signal over Noise · Clarity amid complexity │
│ 4. Relational Proximity · Start with neighbors │
│ 5. Dual Power · Build parallel institutions │
│ 6. Restorative Feedback · Every interaction teaches │
│ 7. Accessible by Default · Design for everyone │
│ │
└─────────────────────────────────────────────────────────────┘
```

---

## Principle 1: Visible Heart

**Make the invisible visible.**

Inspired by Appendix T's concept of the "Visible Heart Grid," this principle holds that civic health should be as legible as a pulse. When something is hidden—sentiment, responsiveness, relationships—it cannot be nurtured or healed.

### Application

| Invisible → | Visible |
|--------------|---------|
| Scattered individual opinions | Aggregated sentiment bars and Φ‑Scores |
| "They never listen" | Promise Tracker showing exactly who acknowledged what |
| Isolated voices | Network visualizations of connections |
| Opaque official responsiveness | Public metrics on acknowledgment and action |
| Hidden community concerns | Trending topics and heat maps |

### Design Implications

- **Φ‑Score everywhere** – The core metric appears on every agenda item, district, and guild profile.
- **Progressive disclosure** – Click any Φ‑Score to reveal its four sub‑metrics.
- **Live updates** – As users interact, scores and visualizations update in real time.
- **No dark corners** – All promises, endorsements, and official responses are public by default.

### Example

On an agenda item page, users see not just a list of notes but a sentiment bar showing the proportion of Support, Oppose, Question, and Proposal. They can see at a glance whether the community is united or divided, and on what.

---

## Principle 2: Living System

**Organic, not industrial.**

CivicNotes should feel alive—responsive, evolving, and connected—not like a sterile corporate dashboard. Forms are rounded, colors are drawn from nature, and interactions have a gentle, human quality.

### Application

| Industrial | Living System |
|------------|---------------|
| Sharp corners, rigid grids | Rounded forms, organic shapes |
| Flat, static colors | Gradients that shift with Φ‑score |
| Abrupt transitions | Gentle animations and fades |
| Generic icons | Custom illustrations rooted in nature |
| Noise (constant alerts) | Signal (meaningful notifications) |

### Design Implications

- **Φ‑Score visualization** – An organic, amoeba‑like form that pulses with health.
- **Color palette** – Earth tones with pops of life: seafoam, amber, terracotta, lavender.
- **Micro‑interactions** – Subtle feedback on actions (a soft glow when a note posts, a gentle pulse when a promise verifies).
- **Data as art** – Network visualizations that resemble mycelial networks or watersheds.

### Example

When a promise is addressed, a subtle animation plays—a small seed transforms into a sprout, symbolizing growth and regeneration. The interaction feels rewarding, not just transactional.

---

## Principle 3: Signal over Noise

**Clarity amid complexity.**

Civic discourse is inherently complex. Our job is to surface what matters and reduce what doesn't. Every element earns its place; if it doesn't serve the user's goals, it doesn't belong.

### Application

| Noise | Signal |
|-------|--------|
| Unfiltered comment streams | Intent tags and sentiment aggregation |
| Duplicate concerns | Clustering of similar notes |
| Low‑quality contributions | Community moderation and flagging |
| Irrelevant content | Personalization and neighborhood filters |
| Information overload | Progressive disclosure, clear hierarchies |

### Design Implications

- **Intent tags** – Every CivicNote includes a clear intent (Support, Oppose, Question, Proposal, Witness), enabling aggregation.
- **Smart defaults** – Users see notes from their neighborhood first, then city‑wide.
- **Filtering** – Robust but intuitive filters help users find what matters.
- **Content hierarchy** – Key information (Φ‑Score, sentiment) is prominent; secondary details are available on demand.

### Example

A user arriving at an agenda item with 200 notes isn't overwhelmed. They see a sentiment bar, top endorsed notes, and a filter to show only "Proposal" notes. The signal is clear; the noise is manageable.

---

## Principle 4: Relational Proximity

**Start with neighbors.**

Democracy is local. CivicNotes prioritizes connection at the neighborhood level, then scales outward. Users should feel the presence of people who share their place and concerns.

### Application

| Distance | Proximity |
|----------|-----------|
| Anonymous, isolated comments | Named neighbors with verified locations |
| City‑wide firehose | Neighborhood‑first feeds |
| Abstract "users" | Real people with profiles, guilds, and histories |
| One‑way communication | Reply threads and network visualization |

### Design Implications

- **Neighbor filter** – By default, users see notes from their verified neighborhood first.
- **Location on profiles** – District or neighborhood is displayed (never exact address).
- **Geographic heat maps** – Show where signatures, notes, and activity are concentrated.
- **Local guild promotion** – Users see guilds active in their area.

### Example

A user's dashboard shows "Trending in Your Neighborhood" before city‑wide trends. When they click an agenda item, they see a badge: "23 notes from your neighbors."

---

## Principle 5: Dual Power

**Build parallel institutions.**

CivicNotes doesn't just comment on power—it builds alternative structures that can eventually transform or replace legacy systems. The design supports collective action, parallel accountability, and community governance.

### Application

| Single Power | Dual Power |
|--------------|------------|
| Commenting only | Proposing, petitioning, promising |
| Individual voices | Guilds and collective endorsements |
| Official records only | Community‑verified Promise Tracker |
| Top‑down governance | Guild Council and Moderation Council |

### Design Implications

- **Clear escalation paths** – From CivicNote → Proposal → Petition → Promise.
- **Guild empowerment** – Guilds have their own dashboards, endorsement powers, and governance roles.
- **Parallel record‑keeping** – Promise Tracker exists alongside (and independent of) official records.
- **Transparency by default** – All dual‑power actions are public, building legitimacy.

### Example

A user who leaves a note can later turn it into a formal proposal using the Regenerative Action Library. That proposal can become a petition, and when the petition succeeds, it auto‑creates a Promise Tracker record—all within the same platform.

---

## Principle 6: Restorative Feedback

**Every interaction teaches.**

Feedback should not just confirm actions but educate and encourage. Users should understand the impact of their participation and feel motivated to continue.

### Application

| Transactional | Restorative |
|---------------|-------------|
| "Note posted" | "Your note was posted. It will help shape discussion on this item." |
| "Promise verified" | "Promise verified! +5 Civic Seeds. This increases your district's responsiveness score." |
| No follow‑up | "Your promise was addressed! Here's how it made a difference." |
| Opaque metrics | Clear explanations of how Φ‑Scores are calculated. |

### Design Implications

- **Explanatory tooltips** – Hover over any Φ‑Score to see sub‑metric breakdowns.
- **Celebratory moments** – When a promise is addressed, users see not just a status change but a story: "This started with your note on April 12..."
- **Impact summaries** – User profiles show "Promises you've influenced" and "Civic Seeds earned."
- **Positive reinforcement** – Encouraging messages for consistent participation.

### Example

After a user verifies a promise, they see: "Thank you for verifying! Your vote helped build trust in this promise. You've now verified 10 promises—keep it up!"

---

## Principle 7: Accessible by Default

**Design for everyone.**

Civic engagement must be inclusive. Accessibility is not an afterthought—it's a fundamental design requirement. The platform must work for people of all abilities, devices, and connection speeds.

### Application

| Exclusive | Inclusive |
|-----------|-----------|
| Desktop‑only | Mobile‑first responsive design |
| Visual‑only | Screen‑reader compatible |
| Fast connection required | Works on slower networks |
| Complex language | Plain language options |
| Single language | Multi‑language support |

### Design Implications

- **WCAG 2.1 AA compliance** – Color contrast, keyboard navigation, screen reader support.
- **Mobile‑first** – All flows designed for small screens first, then scaled up.
- **Offline capability** – Critical information cached; actions queued when offline.
- **Translation ready** – Interface strings externalized for localization.
- **Simple mode** – Optional simplified interface for users with low digital literacy.

### Example

A user with visual impairment can navigate the entire platform using a screen reader. All images have alt text, all interactive elements are properly labeled, and color is never the only indicator of meaning.

---

## Principle in Tension

Sometimes principles conflict. Here's how we prioritize:

| Conflict | Resolution |
|----------|------------|
| **Signal vs. Visible Heart** | If adding visibility creates noise, we prioritize signal. Better to show less clearly than more confusingly. |
| **Living System vs. Accessibility** | Animation and organic forms must never interfere with usability. Accessible defaults override aesthetic preferences. |
| **Dual Power vs. Simplicity** | Powerful features must be introduced gradually, not dumped on users. Progressive onboarding and contextual help are essential. |

---

## Design Tokens

These principles are encoded in our design tokens:

### Color

| Token | Value | Usage |
|-------|-------|-------|
| `--color-ecology` | #2ecc71 | Ecology domain |
| `--color-economics` | #f39c12 | Economics domain |
| `--color-politics` | #e67e22 | Politics domain |
| `--color-spirituality` | #9b59b6 | Spirituality domain |
| `--color-culture` | #e74c3c | Culture domain |
| `--color-ph-high` | #2ecc71 | Φ 71–100 |
| `--color-ph-medium` | #f39c12 | Φ 41–70 |
| `--color-ph-low` | #e74c3c | Φ 0–40 |
| `--color-success` | #27ae60 | Addressed, Verified |
| `--color-warning` | #e67e22 | Disputed, Warning |
| `--color-info` | #3498db | Acknowledged, Info |
| `--color-text` | #2c3e50 | Primary text |
| `--color-background` | #f9f9f9 | Page background |

### Typography

| Token | Value | Usage |
|-------|-------|-------|
| `--font-heading` | "Space Grotesk", sans-serif | Headlines, titles |
| `--font-body` | "Inter", sans-serif | Body text, UI |
| `--font-mono` | "JetBrains Mono", monospace | Evidence, timestamps |
| `--scale-xs` | 0.75rem | Small labels |
| `--scale-sm` | 0.875rem | Secondary text |
| `--scale-base` | 1rem | Body text |
| `--scale-lg` | 1.25rem | Subheadings |
| `--scale-xl` | 1.5rem | Headings |
| `--scale-2xl` | 2rem | Page titles |

### Spacing

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | 0.25rem | Micro spacing |
| `--space-sm` | 0.5rem | Tight spacing |
| `--space-md` | 1rem | Base spacing |
| `--space-lg` | 1.5rem | Relaxed spacing |
| `--space-xl` | 2rem | Section spacing |
| `--space-2xl` | 3rem | Page sections |

### Animation

| Token | Value | Usage |
|-------|-------|-------|
| `--duration-fast` | 0.1s | Micro‑interactions |
| `--duration-base` | 0.2s | Most transitions |
| `--duration-slow` | 0.3s | Page transitions |
| `--easing-default` | ease-in-out | Standard easing |
| `--easing-spring` | cubic-bezier(0.68, -0.55, 0.265, 1.55) | Celebratory animations |

---

## Design Process Checklist

Before shipping any feature, we ask:

- [ ] **Visible Heart** – Does this make something visible that was previously hidden?
- [ ] **Living System** – Does it feel organic and responsive, not industrial?
- [ ] **Signal over Noise** – Does it clarify, not complicate?
- [ ] **Relational Proximity** – Does it connect people to their neighbors?
- [ ] **Dual Power** – Does it build alternative structures or accountability?
- [ ] **Restorative Feedback** – Does it teach and encourage?
- [ ] **Accessible by Default** – Does it work for everyone?

---

## Principles in Practice: Feature Examples

| Feature | Principles Applied |
|---------|-------------------|
| **Φ‑Score** | Visible Heart (1), Living System (2), Signal (3) |
| **Neighbor Filter** | Relational Proximity (4), Signal (3) |
| **Promise Tracker** | Visible Heart (1), Dual Power (5), Restorative Feedback (6) |
| **Guild Endorsements** | Dual Power (5), Relational Proximity (4) |
| **Intent Tags** | Signal (3), Visible Heart (1) |
| **Geographic Heat Maps** | Visible Heart (1), Relational Proximity (4) |
| **Civic Seeds** | Restorative Feedback (6), Dual Power (5) |
| **Screen Reader Support** | Accessible by Default (7) |
| **Organic Φ Animation** | Living System (2), Restorative Feedback (6) |

---

## Conclusion

These principles are not rules to be applied mechanically but values to be interpreted creatively. They should spark discussion, guide tradeoffs, and keep us aligned with our purpose: building a platform that makes democracy visible, relational, and regenerative.

When in doubt, return to the core: **Is this making civic health more visible, more connected, or more accountable?** If the answer is yes, we're on the right path.

---

## Next Steps

- **[Component Library](../component-library/index.md)** – See these principles embodied in reusable components.
- **[User Personas](../ux-guide/user-personas.md)** – Understand who we're designing for.
- **[User Journeys](../ux-guide/user-journey.md)** – See principles in action across complete flows.

Design is never finished—only refined. These principles will evolve as we learn together.
