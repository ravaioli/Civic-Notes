# Appendix: Promise Tracker Algorithm

The Promise Tracker is the accountability engine of CivicNotes—a community‑verified system that tracks whether official acknowledgments lead to tangible action. This appendix explains the technical algorithms that power the Promise Tracker, from proposal through verification to final resolution. It covers scoring, thresholds, decay, fraud prevention, and integration with the Φ‑score.

---

## Core Concepts

| Concept | Definition |
|---------|------------|
| **Promise** | A record linking official acknowledgment to a specific CivicNote, proposal, or petition. |
| **Evidence** | Material (video timestamp, document excerpt, screenshot) supporting a promise. |
| **Verification** | Community voting process to confirm a promise's accuracy. |
| **Verification Threshold** | Number of votes needed to move from Proposed to Verified. |
| **Weighted Voting** | Some votes (guilds, high‑reputation users) count more than others. |
| **Decay** | Promises expire if not verified within a time window. |
| **Dispute** | Challenge to a promise's accuracy, triggering moderator review. |

---

## Promise Lifecycle States
```markdown
Proposed → Verification → Verified → Acknowledged → Addressed
↓ ↓ ↓
Expired Disputed Rejected
```

| State | Definition |
|-------|------------|
| **Proposed** | Initial state; awaiting community verification. |
| **Verification** | Active voting period; accepting verification votes. |
| **Verified** | Threshold reached; community‑confirmed as accurate. |
| **Acknowledged** | Official has publicly responded (optional step). |
| **Addressed** | Action has been taken and verified. |
| **Disputed** | Accuracy challenged; under moderator review. |
| **Rejected** | Found invalid after dispute. |
| **Expired** | Verification period ended without reaching threshold. |

---

## Data Model

```json
{
  "promise": {
    "id": "uuid",
    "sourceType": "civicnote | proposal | petition",
    "sourceId": "uuid",
    "targetOfficialId": "uuid (optional)",
    "targetBodyId": "uuid",
    "evidence": {
      "type": "video | document | text",
      "url": "string",
      "timestamp": "string (for video)",
      "excerpt": "string",
      "uploadedFile": "url (optional)"
    },
    "description": "string",
    "status": "proposed | verification | verified | acknowledged | addressed | disputed | rejected | expired",
    "proposedBy": "userId",
    "proposedAt": "timestamp",
    "verificationDeadline": "timestamp",
    "verifiedAt": "timestamp (optional)",
    "acknowledgedAt": "timestamp (optional)",
    "acknowledgedBy": "userId (optional)",
    "addressedAt": "timestamp (optional)",
    "addressedEvidence": { ... },
    "disputedAt": "timestamp (optional)",
    "disputedBy": ["userIds"],
    "disputeResolution": { ... },
    "voteCount": {
      "yes": 0,
      "no": 0,
      "abstain": 0,
      "weightedYes": 0,
      "weightedNo": 0
    },
    "guildEndorsements": ["guildIds"]
  },
  "verificationVote": {
    "id": "uuid",
    "promiseId": "uuid",
    "userId": "uuid",
    "vote": "yes | no | abstain",
    "weight": "number (1-5 based on reputation)",
    "comment": "string (optional)",
    "votedAt": "timestamp"
  }
}
```
---

## Verification Algorithm

### Step 1: Proposal Submission

When a user proposes a promise:

1. System validates:
   - User is verified (no active suspensions).
   - Source exists (CivicNote, proposal, or petition).
   - Evidence is provided (at least one form).
   - Target official/body is specified.
2. System creates promise record with status = `proposed`.
3. System sets `verificationDeadline` = now + 7 days.
4. Notifications sent to:
   - Source author (if different from proposer).
   - Relevant guilds (based on source content).
   - Users who have expressed interest in the topic.

### Step 2: Verification Period

During the 7‑day verification period:

- Any verified user can cast a verification vote.
- Votes are recorded with weight based on user reputation.
- Users may change their vote until the period ends.

### Step 3: Vote Weight Calculation

Each user has a **vote weight** (1–5) based on:

| Factor | Weight Contribution |
|--------|---------------------|
| **Civic Seeds** (percentile) | 0–2 points |
| **Account age** (years) | 0–1 point |
| **Verification history** (accuracy of past votes) | 0–1 point |
| **Guild membership** (if endorsing guild has endorsed this promise) | +0.5 point |

Formula:
```markdown
baseWeight = 1 + (civicSeedPercentile × 2) + min(accountAgeYears, 1) + accuracyBonus
guildBonus = 0.5 if user's guild has endorsed this promise (max 1 guild counted)
finalWeight = min(5, baseWeight + guildBonus)
```

**Examples:**
- New user, few seeds: weight = 1
- Active user, 2 years, top 20% seeds: weight = 1 + 0.4 + 1 = 2.4 ≈ 2
- Guild leader, top 5% seeds, 3 years, perfect history: weight = 1 + 1 + 1 + 1 = 4 (plus guild bonus possible)

### Step 4: Real‑Time Vote Aggregation

As votes arrive, the system tracks:
```markdown
weightedYes = sum(weight for yes votes)
weightedNo = sum(weight for no votes)
weightedAbstain = sum(weight for abstain votes)
totalWeightedVotes = weightedYes + weightedNo + weightedAbstain

yesPercentage = weightedYes / totalWeightedVotes × 100
```

### Step 5: Threshold Calculation

A promise becomes **Verified** when:
```markdown
weightedYes ≥ VERIFICATION_THRESHOLD
AND
yesPercentage ≥ 60%
```

Where `VERIFICATION_THRESHOLD` is:

| Context | Threshold |
|---------|-----------|
| Default | 5.0 weighted votes |
| Guild‑endorsed promise | 3.0 weighted votes |
| Promise from high‑reputation user (>1000 seeds) | 4.0 weighted votes |

### Step 6: Verification Completion

When threshold is met:

1. Status changes to `verified`.
2. `verifiedAt` timestamp recorded.
3. Notification sent to:
   - Promise proposer.
   - Source author.
   - All who voted.
   - Target official/body.
4. Promise appears in official's dashboard.
5. Responsiveness Φ‑subscore updated (+1.0).

### Step 7: Expiration

If `verificationDeadline` passes without reaching threshold:

1. Status changes to `expired`.
2. Promise remains visible but cannot be voted on.
3. Proposer may resubmit with stronger evidence (counts as new promise).

---

## Acknowledgment Algorithm

### Official Acknowledgment

When an official (or their delegate) acknowledges a promise:

1. Official clicks **"Acknowledge"** in their dashboard.
2. System prompts for optional comment.
3. Status updates to `acknowledged`.
4. `acknowledgedAt` and `acknowledgedBy` recorded.
5. Notification sent to:
   - Promise proposer.
   - All who verified.
   - Source author.
6. Responsiveness Φ‑subscore updated (+2.0).
7. If promise was part of a petition that reached goal, petition status updates to `acknowledged`.

### Automatic Acknowledgment Detection (Future)

For bodies where minutes are published with structured data, the system may auto‑detect acknowledgments by matching keywords to promise descriptions. These would still require community verification.

---

## Addressed Algorithm

### Step 1: Addressed Proposal

Any user can propose marking a promise as **Addressed**:

1. Click **"Mark Addressed"** on promise page.
2. Provide evidence (link, document, photo, description).
3. Submit for verification.

### Step 2: Addressed Verification

Addressed proposals enter a **short verification period** (3 days):

- Same voting rules as initial verification.
- Threshold: 3.0 weighted votes, 60% yes.

### Step 3: Addressed Completion

If verified:

1. Status changes to `addressed`.
2. `addressedAt` and `addressedEvidence` recorded.
3. Notification sent to all involved parties.
4. Responsiveness Φ‑subscore updated (+5.0).
5. All verifiers receive Civic Seeds bonus.
6. Promise appears in "Success Stories" feeds.

### Step 4: Direct Official Marking

Officials may also mark promises as Addressed directly, with evidence. These still undergo verification (same 3‑day period) to maintain community trust.

---

## Dispute Algorithm

### Step 1: Dispute Initiation

Any user may dispute a promise:

- During verification: Click **"Dispute"** on voting interface.
- After verification: Click **"Request Review"** on promise page.

Dispute requires:
- Reason for dispute (required).
- Optional evidence.

### Step 2: Dispute Threshold

A promise enters `disputed` status when:

| Context | Threshold |
|---------|-----------|
| During verification | 2 weighted "no" votes with dispute comments |
| After verification | Single dispute request + moderator review |

### Step 3: Moderator Review

Disputed promises are assigned to a Moderation Council member:

1. Reviewer examines evidence and dispute reason.
2. Reviewer may request additional information.
3. Reviewer presents findings to Council.

### Step 4: Council Decision

Council votes on outcome:

| Outcome | Description | Vote Required |
|---------|-------------|---------------|
| **Uphold** | Promise remains verified | Simple majority |
| **Overrule** | Promise becomes rejected | Simple majority |
| **Remand** | Return for re‑verification with guidance | Simple majority |
| **Modify** | Adjust promise description (rare) | 2/3 majority |

### Step 5: Resolution

Decision recorded in promise record and Case Log. Parties notified.

---

## Time‑Based Decay and Expiration

| Stage | Duration | Action if Not Completed |
|-------|----------|-------------------------|
| Verification | 7 days | Promise expires |
| Addressed verification | 3 days | Addressed proposal expires (promise remains verified) |
| Acknowledged → Addressed | No fixed limit | Promise remains acknowledged indefinitely; can be marked addressed anytime |
| Inactive verified promise | 1 year | Flagged for review; may be archived |

---

## Weighting Factors Summary

| Factor | Weight Impact | Applied To |
|--------|---------------|------------|
| Civic Seeds percentile | 0–2 points | All votes |
| Account age | 0–1 point | All votes |
| Verification history | 0–1 point | All votes |
| Guild endorsement match | +0.5 point | All votes on that promise |
| Guild endorsement (promise) | Threshold reduction | Verification threshold |
| High‑reputation proposer | Threshold reduction | Verification threshold |

---

## Responsiveness Score Contribution

The Promise Tracker directly feeds the **Responsiveness** sub‑score of the Φ‑Score:

| Action | Responsiveness Impact |
|--------|----------------------|
| Promise proposed | +0.5 (to district/body) |
| Promise verified | +1.0 |
| Promise acknowledged | +2.0 |
| Promise addressed | +5.0 |
| Average response time < 14 days | +1.0 bonus |
| 80%+ of promises acknowledged | +2.0 bonus |
| Promise disputed and overruled | −2.0 penalty |

These are aggregated over a 30‑day rolling window.

---

## Fraud Prevention

### Duplicate Detection

System checks for:
- Same evidence submitted for multiple promises.
- Same official statement linked to multiple sources.
- Multiple accounts from same IP voting similarly (flagged for review).

### Reputation Floor

Users must have:
- Minimum 30 days account age to vote.
- Minimum 10 Civic Seeds to propose promises.
- No active sanctions.

### Vote Pattern Analysis

Unusual patterns trigger review:
- Sudden influx of "yes" votes from new accounts.
- Coordinated voting from small group.
- Votes from users with no prior engagement on topic.

### Appeal and Correction

If fraud is detected after verification:
- Case referred to Moderation Council.
- Council may reverse verification.
- Fraudulent voters may face sanctions.

---

## Integration with Other Systems

| System | Integration Point |
|--------|-------------------|
| **Φ‑Score** | Responsiveness sub‑score updated on each promise event. |
| **Petitions** | Petitions that reach goal auto‑create promise records. |
| **Guilds** | Guild endorsements affect vote weighting and thresholds. |
| **Notifications** | Real‑time alerts for status changes, verification needs. |
| **Analytics** | Promise data included in district, guild, and official reports. |
| **Moderation** | Disputed promises routed to Council case system. |

---

## Example Scenarios

### Scenario 1: Simple Verification

1. Alex proposes promise with video evidence.
2. Verification period opens (7 days).
3. 8 users vote:
   - 6 yes (weights: 2,2,1,1,1,1 = 8 weighted)
   - 1 no (weight 2)
   - 1 abstain (weight 1)
4. Weighted yes = 8, threshold = 5 → met.
5. Yes percentage = 8/11 = 73% > 60% → verified.
6. Promise status becomes `verified`.

### Scenario 2: Guild‑Endorsed Fast Track

1. Jamie proposes promise; Safe Streets Guild endorses.
2. Threshold reduced to 3.0.
3. 3 guild members vote yes (weights: 3,2,2 = 7 weighted).
4. Threshold met immediately.
5. Promise verified in 1 day.

### Scenario 3: Disputed Promise

1. Priya proposes promise with unclear evidence.
2. During verification, 2 users vote "no" with comments questioning accuracy.
3. Dispute threshold met (2 weighted no votes with comments).
4. Status changes to `disputed`.
5. Moderator reviews, finds evidence insufficient.
6. Council votes to overrule → status becomes `rejected`.

### Scenario 4: Addressed Verification

1. Verified promise about traffic study exists for 3 months.
2. City releases study; Taylor marks promise addressed with link.
3. 3‑day verification period opens.
4. 5 users verify (weights total 9).
5. Threshold met → status becomes `addressed`.
6. All participants receive Civic Seeds; Φ‑score increases.

---

## Performance Considerations

| Operation | Frequency | Optimization |
|-----------|-----------|--------------|
| Vote recording | Real‑time | Indexed by promiseId, userId |
| Threshold checking | On each vote | Cached weighted totals |
| Expiration checks | Daily cron job | Batch update expired promises |
| Notification triggers | Real‑time | Queue system for async sending |
| Analytics aggregation | Daily | Pre‑computed summaries |

---

## API Endpoints (Summary)

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/promises` | POST | Create new promise |
| `/api/promises/{id}` | GET | Get promise details |
| `/api/promises/{id}/votes` | POST | Cast verification vote |
| `/api/promises/{id}/acknowledge` | POST | Official acknowledgment |
| `/api/promises/{id}/addressed` | POST | Propose addressed status |
| `/api/promises/{id}/dispute` | POST | File dispute |
| `/api/promises/feed` | GET | Personalized promise feed |

---

## Future Enhancements

| Enhancement | Description |
|-------------|-------------|
| **AI‑assisted matching** | Auto‑detect acknowledgments from meeting transcripts |
| **Blockchain timestamping** | Optional hash storage for tamper‑proof evidence |
| **Reputation decay** | Older votes weigh less over time |
| **Cross‑platform promises** | Track promises made outside CivicNotes (e.g., in media) |
| **Predictive scoring** | Estimate likelihood of promise being addressed |

---

## Summary: Promise Tracker by the Numbers

| Metric | Typical Value |
|--------|---------------|
| Verification period | 7 days |
| Addressed verification | 3 days |
| Default threshold | 5.0 weighted votes |
| Guild‑endorsed threshold | 3.0 weighted votes |
| Vote weight range | 1–5 |
| Responsiveness Φ impact (addressed) | +5.0 |
| Maximum response time score | 100 (0 days) |
| Minimum response time score | 0 (50+ days) |

---

## Next Steps

- **[Φ‑Score Calculation](ph-score-calculation.md)** – See how promises affect civic health.
- **[Promise Tracker UX](../user-guide/tracking-promises.md)** – User‑facing guide.
- **[Moderation Council](moderation-council.md)** – Dispute resolution process.

The Promise Tracker algorithm transforms accountability from a fuzzy ideal into a precise, measurable, and trustworthy system. Every verified promise is a small victory for transparency and trust.
