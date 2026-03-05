# CivicNotes

**Social platform for regenerative civic engagement.**

CivicNotes transforms how communities interact with local government. By making public meetings, agendas, and decisions visible, accountable, and actionable, it empowers residents, organizations, and officials to co‑create a healthier, more participatory democracy.

<img src="https://github.com/ravaioli/Civic-Notes/blob/main/docs/CivicNote.png" alt="CivicNotes" style="width:75%; height:auto;">
---

## Vision

We envision a world where every resident has the tools to understand, influence, and track the decisions that shape their community. CivicNotes weaves together transparent data, collective intelligence, and accountable feedback loops to make local governance a living, responsive part of everyday life—a true **Visible Heart** for the city.

Inspired by the [Solarpunk Mandala](https://github.com/ravaioli/solarpunk-mandala), CivicNotes embodies principles of dual power, regenerative economics, and consciousness‑first design.

---

## Key Features

| Feature | Description |
|---------|-------------|
| **Φ‑Score** | A composite metric (0–100) measuring civic health – participation, clarity, responsiveness, and connections. |
| **CivicNotes** | Short public comments on agenda items with intent tags (Support, Oppose, Question, Proposal, Witness). |
| **Promise Tracker** | Community‑verified system tracking official acknowledgments and actions. |
| **Guilds** | Verified collectives that endorse content, sponsor proposals, and participate in platform governance. |
| **Petitions** | Formal expressions of community will with verified signatures; auto‑create promises when goals are met. |
| **Regenerative Actions** | A library of pre‑defined, strategically aligned intervention templates. |
| **Official Dashboard** | Specialized tools for elected officials and staff to monitor sentiment, respond to promises, and engage with petitions. |
| **Community Governance** | Moderation Council and Guild Council ensure transparent, distributed decision‑making. |

---

## Core Concepts

| Concept | Description |
|---------|-------------|
| **Φ‑Score** | The visible heartbeat of civic discourse – see [Φ‑Score Calculation](appendices/ph-score-calculation.md). |
| **CivicNote** | The basic unit of conversation – see [Leaving Notes](user-guide/leaving-notes.md). |
| **Promise Tracker** | Accountability engine – see [Tracking Promises](user-guide/tracking-promises.md) and [Promise Tracker Algorithm](appendices/promise-tracker-algorithm.md). |
| **Guilds** | Collective power – see [Creating a Guild](guild-guide/creating-guild.md). |
| **Petitions** | Organized will – see [Petitions](user-guide/petitions.md). |
| **Regenerative Actions** | Solution templates – see [Action Library](../actions/overview.md). |

---

## User Personas

CivicNotes is designed for a diverse range of participants:

| Persona | Role | Primary Goal |
|---------|------|--------------|
| **Alex** | Resident | Understand and influence local decisions. |
| **Jamal** | Guild Leader | Organize collective action and build power. |
| **Priya** | Power User | Deeply engage and track impact across issues. |
| **Martinez** | Elected Official | Understand constituents and respond accountably. |
| **Taylor** | Staff | Support official engagement and manage workflow. |
| **Jordan** | New User | Learn the platform and get started easily. |
| **Casey** | Moderator | Maintain community health and resolve disputes. |

See [User Personas](ux-guide/user-personas.md) for detailed profiles.

---

## Platform Governance

CivicNotes is governed by its community through two primary bodies:

| Body | Role | Composition |
|------|------|-------------|
| **Guild Council** | Legislative – sets policy, allocates resources, elects moderators. | One representative from each verified guild. |
| **Moderation Council** | Judicial – resolves disputes, enforces Code of Conduct. | 7 members elected by the Guild Council. |

See [Guild Verification](governance/guild-verification.md) and [Moderation Council](governance/moderation-council.md) for details.

---

## Documentation Structure

All documentation is written in Markdown and organized in the `/docs` folder:
```markdown
docs/
├── index.md # Landing page (GitHub Pages)
├── overview.md # High‑level introduction
├── user-guide/ # For citizens and general users
│ ├── getting-started.md
│ ├── core-concepts.md
│ ├── finding-agenda.md
│ ├── leaving-notes.md
│ ├── tracking-promises.md
│ ├── petitions.md
│ └── glossary.md
├── guild-guide/ # For guild members and leaders
│ ├── creating-guild.md
│ ├── guild-dashboard.md
│ ├── endorsements.md
│ ├── proposals.md
│ ├── member-management.md
│ └── guild-governance.md
├── official-guide/ # For verified government users
│ ├── verification.md
│ ├── dashboard-overview.md
│ ├── responding-to-promises.md
│ ├── engaging-with-petitions.md
│ └── best-practices.md
├── ux-guide/ # UX philosophy and detailed flows
│ ├── design-principles.md
│ ├── user-personas.md
│ └── user-journey.md
├── component-library/ # Reusable UI components
│ ├── index.md
│ ├── navigation.md
│ ├── cards.md
│ ├── forms.md
│ ├── data-viz.md
│ ├── notifications.md
│ └── design-tokens.md
├── governance/ # Platform governance models
│ ├── guild-verification.md
│ ├── moderation-council.md
│ ├── dispute-resolution.md
│ └── code-of-conduct-enforcement.md
├── technical/ # For developers and integrators
│ ├── architecture-overview.md
│ ├── data-models.md
│ ├── legistar-integration.md
│ ├── authentication.md
│ ├── api-docs.md
│ └── deployment.md
├── appendices/ # Extended references
│ ├── ph-score-calculation.md
│ ├── promise-tracker-algorithm.md
│ ├── accessibility.md
│ └── glossary.md
└── assets/ # Images, diagrams, icons
├── diagrams/
└── icons/
```

---

## Technology Stack (Planned)

| Layer | Technology |
|-------|------------|
| **Frontend** | React / Next.js, TypeScript, Tailwind CSS |
| **Backend** | Node.js / Express, PostgreSQL |
| **Authentication** | OAuth 2.0, Magic Links, SMS verification |
| **Real‑time** | WebSockets (Socket.io) |
| **Integrations** | Legistar / Granicus API |
| **Hosting** | Vercel (frontend), Heroku / AWS (backend) |
| **Documentation** | GitHub Pages / MkDocs |

---

## Contributing

We welcome contributions! Whether you're a designer, developer, writer, or community organizer, there are many ways to help.

- **Report bugs** or **suggest features** via [Issues](https://github.com/your-org/civicnotes/issues).
- **Improve documentation** – see our [Contributing Guide](CONTRIBUTING.md).
- **Join the conversation** in our [Community Forum](https://community.civicnotes.org) (coming soon).

Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before participating.

---

## License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details. Documentation is licensed under [Creative Commons Attribution‑ShareAlike 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

---

## Acknowledgments

CivicNotes is deeply inspired by the [Solarpunk Mandala](https://github.com/ravaioli/solarpunk-mandala) and the work of many thinkers and practitioners building regenerative futures. Special thanks to the open‑source community and everyone who believes that another world is possible—and that we can code it into being.

---

**Let's make democracy visible, together.**
