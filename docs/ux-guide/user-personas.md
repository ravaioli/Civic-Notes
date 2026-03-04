# User Personas

Understanding our users is essential to designing a platform that serves them effectively. These personas represent the diverse individuals and groups who interact with CivicNotes—their goals, frustrations, motivations, and how they engage with the platform. They are fictional but grounded in real observations and community input.

---

## Why Personas Matter

Personas help us:

- **Empathize** with different user perspectives.
- **Make design decisions** based on real needs, not assumptions.
- **Identify gaps** in functionality or experience.
- **Communicate** about users across the design and development team.
- **Test designs** against representative scenarios.

---

## The CivicNotes Persona Ecosystem
```markdown
┌─────────────────────────────────────────────────────────────┐
│ │
│ ┌─────────────────┐ │
│ │ Alex │ │
│ │ Resident │ │
│ └────────┬────────┘ │
│ │ │
│ interacts with │ collaborates with │
│ ▼ │ ▼ │
│ ┌─────────────────┐ │ ┌─────────────────┐ │
│ │ Jamal │◄─────┼──────│ Priya │ │
│ │ Guild Leader │ │ │ Power User │ │
│ └─────────────────┘ │ └─────────────────┘ │
│ │ │ │ │
│ │ │ │ │
│ ▼ ▼ ▼ │
│ ┌─────────────────────────────────────────────────┐ │
│ │ Martinez · Taylor · Jordan │ │
│ │ Officials & Staff │ │
│ └─────────────────────────────────────────────────┘ │
│ │
│ influences · governs · supports │
│ ▼ │
│ ┌─────────────────────┐ │
│ │ Casey │ │
│ │ Moderator │ │
│ └─────────────────────┘ │
│ │
└─────────────────────────────────────────────────────────────┘
```

---

## The Core Personas

| Persona | Role | Primary Goal |
|---------|------|--------------|
| **Alex** | Resident | Understand and influence local decisions. |
| **Jamal** | Guild Leader | Organize collective action and build power. |
| **Priya** | Power User | Deeply engage and track impact across issues. |
| **Martinez** | Elected Official | Understand constituents and respond accountably. |
| **Taylor** | Staff | Support official engagement and manage workflow. |
| **Jordan** | New User | Learn the platform and get started easily. |
| **Casey** | Moderator | Maintain community health and resolve disputes. |

---

## Alex · The Concerned Resident
```markdown
┌─────────────────────────────────────────────────────────────────┐
│ ALEX │
│ Age: 38 · District 3 · Verified Resident │
│ Occupation: Teacher · Parent of two │
│ Tech Comfort: Medium (uses social media, apps) │
│ Time Available: 15–30 minutes, a few times per week │
└─────────────────────────────────────────────────────────────────┘
```

### Bio

Alex moved to the neighborhood five years ago and cares deeply about making it safe and welcoming for their kids. They attend occasional City Council meetings but often find them confusing and time‑consuming. Alex wants to stay informed and have a voice, but doesn't have hours to devote to civic engagement.

### Goals

- **Stay informed** about issues affecting their neighborhood.
- **Voice concerns** simply and quickly.
- **Understand** what others in the community think.
- **Know if anyone is listening**—see impact of their participation.

### Frustrations

- Meeting agendas are long and hard to navigate.
- It's unclear which items actually matter.
- "They never listen"—hard to tell if input makes a difference.
- Time constraints prevent deeper involvement.

### Motivations

- Making the neighborhood safer for their kids.
- Connecting with neighbors who share concerns.
- Feeling that their voice matters.

### How Alex Uses CivicNotes

| Frequency | Actions |
|-----------|---------|
| **Weekly** | Check upcoming meetings, scan items with high Φ‑score or neighbor activity. |
| **As needed** | Leave CivicNotes on items that matter (using Proposal or Support intents). |
| **Occasionally** | Sign petitions endorsed by neighbors or guilds. |
| **Rarely** | Verify promises, attend meetings. |

### Alex's Journey

1. Hears about a zoning change at 5th and Main from a neighbor.
2. Logs in, finds the agenda item, sees 34 notes from neighbors.
3. Reads a few, sees the Safe Streets Guild has endorsed a proposal.
4. Leaves their own note: "I walk my kids here daily. We need a traffic study."
5. Later, gets a notification that a promise was created from their note.
6. Feels heard—shares with neighbors.

### Key Needs from Platform

- Clear, simple agenda navigation.
- At‑a‑glance understanding of community sentiment.
- Easy note composition with intent tags.
- Notifications when their input leads to action.
- Connection to neighbors and relevant guilds.

---

## Jamal · The Guild Leader
```markdown
┌─────────────────────────────────────────────────────────────────┐
│ JAMAL │
│ Age: 45 · District 5 · Verified Resident │
│ Role: Founder, Safe Streets Guild │
│ Occupation: Architect · Community organizer │
│ Tech Comfort: High (uses multiple tools, coordinates online) │
│ Time Available: 5–10 hours per week │
└─────────────────────────────────────────────────────────────────┘
```

### Bio

Jamal has been organizing around pedestrian safety for years. He founded the Safe Streets Guild to bring together neighbors who care about crosswalks, traffic calming, and safe routes to school. He's strategic, patient, and knows how to build coalitions.

### Goals

- **Build collective power**—amplify individual voices through the guild.
- **Coordinate action**—endorse notes, create proposals, launch petitions.
- **Track impact**—see which efforts lead to change.
- **Influence platform governance**—participate in Guild Council.
- **Recruit and engage members**—keep the guild active and focused.

### Frustrations

- Dispersed communication across email, text, social media.
- Hard to track what the guild has endorsed or proposed.
- Members have varying levels of commitment.
- Official responses are slow or nonexistent.

### Motivations

- Making streets safer for everyone.
- Building a respected, effective organization.
- Empowering others to lead.

### How Jamal Uses CivicNotes

| Frequency | Actions |
|-----------|---------|
| **Daily** | Check guild dashboard, review endorsement queue, respond to member requests. |
| **Weekly** | Facilitate guild discussions, vote on endorsements, create proposals from regenerative actions. |
| **Monthly** | Attend Guild Council meetings, review analytics, plan strategy. |
| **As needed** | Launch petitions, coordinate with other guilds, respond to media inquiries. |

### Jamal's Journey

1. Guild member suggests endorsing a note about 5th and Main.
2. Jamal sees it in the endorsement queue, opens discussion.
3. Members vote, endorsement passes.
4. Jamal uses the Regenerative Action Library to create a formal proposal based on the note.
5. Guild endorses the proposal; Jamal submits it to the City Council.
6. When a council member acknowledges it, a promise is created.
7. Jamal tracks the promise, reminds members to verify, celebrates when addressed.

### Key Needs from Platform

- Comprehensive guild dashboard.
- Collaborative proposal tools.
- Endorsement queue with discussion and voting.
- Analytics on guild impact.
- Connection to other guilds and officials.

---

## Priya · The Power User
```markdown
┌─────────────────────────────────────────────────────────────────┐
│ PRIYA │
│ Age: 32 · District 7 · Verified Resident │
│ Occupation: Data analyst · Community researcher │
│ Tech Comfort: Very high (technical, loves data) │
│ Time Available: 5–7 hours per week │
└─────────────────────────────────────────────────────────────────┘
```

### Bio

Priya is deeply engaged in multiple issues—housing, transit, climate. She's not a guild leader but is highly active: leaving notes, verifying promises, signing petitions, and tracking outcomes. She loves data and uses CivicNotes' analytics to understand trends and hold officials accountable.

### Goals

- **Track everything**—follow issues across multiple agenda items and bodies.
- **Verify promises**—help build the accountability record.
- **Analyze trends**—understand what's working and what's not.
- **Share insights**—with guilds, officials, and the community.
- **Maximize impact**—focus energy where it matters most.

### Frustrations

- Inconsistent engagement from others.
- Hard to get complete data on official responsiveness.
- Some promises languish without verification.
- Limited tools for cross‑issue analysis.

### Motivations

- Evidence‑based advocacy.
- Holding power accountable.
- Building a public record of civic health.

### How Priya Uses CivicNotes

| Frequency | Actions |
|-----------|---------|
| **Daily** | Scan new promises, verify where needed, check district Φ‑score trends. |
| **Weekly** | Review all agenda items, leave notes with data‑backed proposals, download analytics. |
| **Monthly** | Generate reports, share with guilds, attend meetings. |
| **As needed** | File disputes on inaccurate promises, request data exports. |

### Priya's Journey

1. Priya notices the Φ‑score for District 7 dropping.
2. She drills into the data, sees Responsiveness sub‑score is low.
3. She reviews pending promises, finds several unacknowledged.
4. She posts in relevant guilds: "These promises need attention—can we push?"
5. She files a public records request for data on official response times.
6. She shares findings in a CivicNote, sparking discussion.

### Key Needs from Platform

- Advanced analytics and data export.
- Promise Tracker with filtering and search.
- Cross‑item and cross‑body tracking.
- Notification customization.
- API access for external analysis.

---

## Martinez · The Elected Official
```markdown
┌─────────────────────────────────────────────────────────────────┐
│ MARTINEZ │
│ Age: 52 · District 3 · City Council Member │
│ Occupation: Former nonprofit director │
│ Tech Comfort: Medium (uses email, social media, but busy) │
│ Time Available: 1–2 hours per week for platform engagement │
└─────────────────────────────────────────────────────────────────┘
```

### Bio

Martinez is in their second term on the City Council. They genuinely care about constituent input but are overwhelmed by the volume of communication—email, phone, social media, in‑person. They want to be responsive but need efficient tools.

### Goals

- **Understand priorities**—what do constituents actually care about?
- **Respond efficiently**—acknowledge input without drowning.
- **Track commitments**—follow through on promises.
- **Demonstrate responsiveness**—build trust for reelection.
- **Prepare for meetings**—know what issues will arise.

### Frustrations

- Too many channels, too much noise.
- Hard to tell what's a trend vs. an outlier.
- Previous promises get lost in the shuffle.
- Staff has limited time to help.

### Motivations

- Serving constituents effectively.
- Maintaining a reputation as responsive.
- Winning reelection (honest).

### How Martinez Uses CivicNotes

| Frequency | Actions |
|-----------|---------|
| **Daily (5 min)** | Check notifications, scan new promises mentioning them. |
| **Weekly (30 min)** | Review upcoming meetings with analytics, respond to pending promises. |
| **Monthly** | Check district Φ‑score trends, review staff delegate actions. |
| **As needed** | Acknowledge petitions, mark promises addressed. |

### Martinez's Journey

1. Morning check: sees 3 new verified promises.
2. Reviews each—one about traffic study, one about library hours, one about park funding.
3. Acknowledges the traffic study promise with a note: "Staff is reviewing; will report at next meeting."
4. Asks staff to draft response for library hours.
5. Before next council meeting, reviews agenda items with high Φ‑scores and many notes.
6. Notes that 5th and Main has strong opposition; prepares questions for staff.

### Key Needs from Platform

- Streamlined official dashboard.
- Promise inbox with clear prioritization.
- Agenda analytics with sentiment summaries.
- Staff delegation capabilities.
- Mobile access for on‑the‑go responses.

---

## Taylor · The Government Staff
```markdown
┌─────────────────────────────────────────────────────────────────┐
│ TAYLOR │
│ Age: 29 · City Clerk's Office │
│ Role: Supports Council Member Martinez and Transportation Committee │
│ Tech Comfort: High │
│ Time Available: 3–5 hours per week delegated to platform │
└─────────────────────────────────────────────────────────────────┘
```

### Bio

Taylor works in the City Clerk's Office, supporting multiple council members and committees. They're responsible for monitoring correspondence, preparing briefing materials, and ensuring official records are accurate. They're efficient, organized, and often the person behind the scenes making things work.

### Goals

- **Manage official engagement** efficiently across multiple officials.
- **Prepare accurate briefings** for meetings.
- **Track promises** and ensure follow‑through.
- **Maintain official records** in sync with platform data.
- **Support multiple officials** with consistent quality.

### Frustrations

- Juggling multiple officials' preferences and priorities.
- Manual data entry between systems.
- Last‑minute requests before meetings.
- Ensuring responses are timely and on‑brand.

### Motivations

- Doing their job well and efficiently.
- Helping officials look good and serve constituents.
- Building systems that reduce fire‑drills.

### How Taylor Uses CivicNotes

| Frequency | Actions |
|-----------|---------|
| **Daily** | Monitor promise inbox for all supported officials, draft responses for review. |
| **Weekly** | Prepare meeting briefings with Φ‑scores and top notes, update tracking systems. |
| **As needed** | Respond to petitions on behalf of officials (with permission), mark promises addressed. |

### Taylor's Journey

1. Taylor logs in and sees three new promises for Martinez.
2. Drafts responses for each, flags one that needs legal review.
3. Martinez reviews and approves; Taylor posts acknowledgments.
4. Before transportation committee meeting, Taylor pulls analytics: 5th and Main has 45 notes, mostly opposed.
5. Prepares a one‑page summary for committee members.
6. After meeting, updates promise statuses based on actions taken.

### Key Needs from Platform

- Multi‑official dashboard view.
- Draft response tools with approval workflow.
- Easy analytics export for briefing materials.
- Integration with existing records systems.
- Clear audit trail of all actions.

---

## Jordan · The New User
```markdown
┌─────────────────────────────────────────────────────────────────┐
│ JORDAN │
│ Age: 24 · District 9 · Recently moved to the city │
│ Occupation: Barista · Renter │
│ Tech Comfort: High (heavy social media user) │
│ Time Available: Variable, but willing to learn │
└─────────────────────────────────────────────────────────────────┘
```

### Bio

Jordan just moved to the city for work. They're interested in local issues—especially housing and transit—but don't know where to start. They've never been to a public meeting and find local government intimidating. A friend recommended CivicNotes.

### Goals

- **Learn** how local government works.
- **Find** issues they care about.
- **Participate** without feeling overwhelmed.
- **Connect** with others who share interests.

### Frustrations

- Local government is confusing—jargon, processes, bodies.
- Hard to know where to start.
- Afraid of saying something "wrong."
- Unsure if participation matters.

### Motivations

- Feeling like a real part of their new community.
- Making their neighborhood better.
- Learning how things work.

### How Jordan Uses CivicNotes

| Frequency | Actions |
|-----------|---------|
| **First visit** | Complete onboarding, verify neighborhood, explore dashboard. |
| **First week** | Browse agenda items, read notes, follow a guild. |
| **First month** | Leave first note, sign a petition, verify a promise. |
| **Ongoing** | Gradually increase engagement as comfort grows. |

### Jordan's Journey

1. Jordan signs up, verifies their neighborhood via SMS.
2. Takes the guided tour, learns about Φ‑score and intent tags.
3. Sees a trending item about affordable housing—reads notes.
4. Follows the Housing Justice Guild.
5. A few days later, sees a petition from that guild and signs it.
6. Gets a notification when the petition reaches its goal—feels part of something.

### Key Needs from Platform

- Clear, welcoming onboarding.
- Progressive disclosure—don't overwhelm.
- Plain language explanations.
- Guided pathways based on interests.
- Encouraging feedback for early actions.

---

## Casey · The Moderator
```markdown
┌─────────────────────────────────────────────────────────────────┐
│ CASEY │
│ Age: 41 · District 2 · Verified Resident │
│ Role: Moderation Council member │
│ Occupation: Mediator · Conflict resolution specialist │
│ Tech Comfort: Medium │
│ Time Available: 5–8 hours per week (volunteer role) │
└─────────────────────────────────────────────────────────────────┘
```

### Bio

Casey has years of experience in community mediation and restorative justice. They were nominated by a guild and elected to the Moderation Council. They believe in fair process, listening deeply, and helping people find resolution. They're patient, thoughtful, and committed to the health of the platform.

### Goals

- **Resolve disputes** fairly and efficiently.
- **Uphold Code of Conduct** consistently.
- **Protect community trust** in moderation processes.
- **Support restorative outcomes** where possible.
- **Learn and improve** processes over time.

### Frustrations

- Limited time for complex cases.
- Emotional intensity of some disputes.
- Balancing transparency with confidentiality.
- Ensuring consistency across cases.

### Motivations

- Keeping the community healthy and safe.
- Modeling constructive conflict resolution.
- Serving the community that elected them.

### How Casey Uses CivicNotes

| Frequency | Actions |
|-----------|---------|
| **Daily** | Check case queue, triage new reports. |
| **Weekly** | Attend Council meetings, deliberate on active cases, write decisions. |
| **As needed** | Facilitate mediations, consult with other Council members, update case log. |

### Casey's Journey

1. New dispute filed: promise accuracy challenged.
2. Casey is assigned as primary reviewer.
3. Reviews evidence, contacts both parties for input.
4. Presents findings to full Council; discussion.
5. Council votes to uphold the promise with clarification.
6. Casey writes decision, posts to Case Log, notifies parties.
7. Reflects on case in monthly Council debrief.

### Key Needs from Platform

- Case management system with clear workflow.
- Confidential communication tools.
- Decision templates and case log publishing.
- Access to Code of Conduct and past precedents.
- Calendar for meetings and deadlines.

---

## Secondary Personas

| Persona | Role | Key Need |
|---------|------|----------|
| **Journalist** | Local reporter | Find story leads, track trends, download data. |
| **Researcher** | Academic studying civic engagement | Access anonymized data, export for analysis. |
| **Tech Volunteer** | Helps neighbors use platform | Simple explainers, bulk actions, offline tools. |
| **Youth Organizer** | Engages young residents | Mobile‑first, social features, simplified onboarding. |
| **Nonprofit Leader** | Runs advocacy organization | Guild tools, coalition building, impact reporting. |

---

## Persona Usage Guidelines

### When to Use Personas

- **Feature design** – "How would Alex use this feature?"
- **Prioritization** – "Which personas benefit most from this?"
- **Usability testing** – Recruit participants matching personas.
- **Design reviews** – "Would this work for Jordan?"
- **Documentation** – Reference personas in specs and guides.

### How to Reference Personas

| Format | Example |
|--------|---------|
| **By name** | "Alex needs a simpler way to find agenda items." |
| **By role** | "Guild leaders like Jamal need collaborative tools." |
| **By scenario** | "In the new user scenario (Jordan), onboarding should be guided." |

### Keeping Personas Alive

- Review annually and update based on user research.
- Add new personas as platform evolves.
- Retire personas that no longer represent core users.

---

## Persona Matrix

| Feature | Alex | Jamal | Priya | Martinez | Taylor | Jordan | Casey |
|---------|------|-------|-------|----------|--------|--------|-------|
| Agenda browsing | High | High | High | High | High | Medium | Low |
| Leaving notes | High | Medium | High | Low | Low | Medium | Low |
| Promise verification | Low | High | High | Low | Low | Low | Medium |
| Guild tools | Low | High | Medium | Low | Low | Medium | Low |
| Analytics | Low | High | High | Medium | High | Low | Medium |
| Official dashboard | N/A | N/A | N/A | High | High | N/A | N/A |
| Moderation tools | N/A | N/A | N/A | N/A | N/A | N/A | High |
| Petitions | Medium | High | High | Low | Low | Medium | Low |
| Mobile access | High | High | High | High | Medium | High | Low |

---

## From Personas to Design

These personas inform every aspect of CivicNotes design:

- **Information architecture** – Alex needs intuitive navigation; Priya needs deep search.
- **Visual design** – Jordan needs clarity; Martinez needs efficiency.
- **Content strategy** – Plain language for Jordan; data depth for Priya.
- **Feature prioritization** – Guild tools for Jamal; moderation tools for Casey.
- **Onboarding** – Progressive disclosure for Jordan; quick start for officials.

---

## Next Steps

- **[User Journeys](user-journey.md)** – See how these personas move through the platform.
- **[Design Principles](design-principles.md)** – The values guiding design for all personas.
- **[Component Library](../component-library/index.md)** – UI elements designed for these users.

Personas are living documents. As we learn more about our users, these portraits will evolve—but their purpose remains constant: keeping real people at the center of everything we build.
