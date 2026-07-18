# Heimdall — UI and Product Design Specification

**Purpose:** Source of truth for creating the Heimdall mockup UI  
**Current phase:** Documentation  
**Next phases:** Mock designs, then prototype

> Heimdall turns a question scattered across enterprise systems into a visual answer shaped for the person asking and backed by evidence they are authorized to inspect.

---

## 1. Product idea

Enterprise knowledge does not live in one place. It is scattered across systems such as Salesforce, Zoho, SAP, Google Drive, Microsoft Azure, SharePoint, Teams, GitHub, Slack, Jira, Confluence, and ServiceNow.

A user should not need to know which system contains the answer.

Heimdall:

1. Receives a question.
2. Understands who is asking.
3. Selects the most relevant authorized knowledge sources.
4. Gathers evidence.
5. Processes the evidence into grounded facts.
6. Builds an answer for that person.
7. Converts the answer into a visual brief.

### Product promise

**Ask one enterprise question. Receive a visual answer shaped for you and backed by evidence you can inspect.**

### What Heimdall is not

- Not another generic chatbot
- Not a replacement for enterprise systems of record
- Not an employee-surveillance product
- Not a dashboard containing every possible metric
- Not an opaque AI answer with citations appended at the end

Heimdall is a decision surface over authorized enterprise knowledge.

---

## 2. Brand concept

In Norse mythology, Heimdall is the vigilant guardian who watches across realms. The product uses that metaphor carefully: each enterprise platform is a distinct knowledge realm, and Heimdall assembles the relevant views without violating their access boundaries.

### Brand line

**Enterprise answers you can see and defend.**

### Supporting lines

- Across every system. The right answer for you.
- Every authorized source. One clear answer. The right view.
- One question. The right perspective.

### All-seeing body

The primary brand visual is an original mythological guardian whose body contains multiple refined eye or lens motifs.

Each lens represents an authorized view into a knowledge realm:

- Customer lens: Salesforce and Zoho CRM
- Financial lens: SAP S/4HANA
- Support lens: Zoho Desk and ServiceNow
- Document lens: Google Drive and SharePoint
- Engineering lens: GitHub, Jira, Confluence, and Azure DevOps
- Communication lens: Slack and Microsoft Teams

The visual should communicate governed perception, not unrestricted surveillance.

### Brand restrictions

- Do not resemble Marvel’s Heimdall, an actor, or an existing film costume.
- Do not use rainbow bridges, superhero poses, copied iconography, or weapons as the focal point.
- Do not use grotesque biological eyes or body horror.
- Do not make mythology dominate the enterprise product story.
- Use an original public-domain mythological interpretation.

---

## 3. Build sequence

Work must happen in this order:

### Phase 1 — Documentation

Define the product story, personas, source behavior, screen inventory, information hierarchy, components, interactions, visual system, and canonical demo data.

### Phase 2 — Mock designs

Create high-fidelity desktop mockups from this document. The mock should prove the idea without requiring a working backend.

### Phase 3 — Prototype

Replace mock data and simulated transitions with a working pipeline. The prototype implements the approved mock rather than redesigning the product during development.

---

## 4. First conclusion: who is the answer for?

Before building the answer, Heimdall determines who the answer is for.

The signed-in user is resolved into one of four personas:

| Persona | Typical users | Answer treatment |
|---|---|---|
| **Developer** | Software engineers, platform engineers, individual contributors | Root cause, technical timeline, code references, incidents, and remediation |
| **Manager** | Engineering managers, delivery managers, account managers | Status, blockers, owners, dates, dependencies, and escalation path |
| **Senior** | Staff engineers, principal engineers, solution architects | Cross-system context, trade-offs, decision history, dependencies, and systemic risk |
| **CxO** | CEO, CTO, CIO, CRO, CFO, business-unit leaders | Business impact, money, customer risk, strategic options, and the decision required |

### Identity treatment

The application header always shows:

- User avatar
- Name
- Job title
- Department
- Concluded persona

Example:

> **Priya Natarajan**  
> VP Sales · Revenue · EMEA  
> **CxO view**

For the mockup and hackathon demo, display a persona switcher:

`Developer | Manager | Senior | CxO`

In production, identity selects the initial persona. The switcher changes the viewing lens; it never bypasses permissions.

---

## 5. Persona-driven knowledge selection

Different roles rely on different parts of the enterprise knowledge layer.

A developer generally needs more depth from GitHub, Slack, Jira, and Azure DevOps than from an executive board deck. A CxO generally needs more depth from Salesforce, SAP, Power BI, and executive documents than from a pull request.

Persona sets source priority, retrieval depth, answer vocabulary, and visual treatment.

### Source priority matrix

| Enterprise source | Developer | Manager | Senior | CxO |
|---|---:|---:|---:|---:|
| **GitHub** | Primary | Contextual | Primary | Summary only |
| **Slack** | Primary | Secondary | Secondary | Contextual |
| **Jira** | Primary | Primary | Primary | Summary only |
| **Confluence** | Secondary | Primary | Primary | Summary only |
| **Azure DevOps** | Primary | Secondary | Primary | Summary only |
| **Microsoft Teams** | Secondary | Primary | Secondary | Secondary |
| **SharePoint** | Contextual | Secondary | Secondary | Primary |
| **Google Drive** | Contextual | Secondary | Secondary | Primary |
| **Salesforce** | Contextual | Secondary | Contextual | Primary |
| **Zoho CRM** | Contextual | Secondary | Contextual | Secondary |
| **Zoho Desk** | Secondary | Primary | Secondary | Summary only |
| **SAP S/4HANA** | Contextual | Contextual | Contextual | Primary |
| **ServiceNow** | Secondary | Secondary | Primary | Summary only |
| **Power BI** | Contextual | Secondary | Secondary | Primary |

Definitions:

- **Primary:** searched deeply and shown prominently
- **Secondary:** searched when relevant
- **Contextual:** used when the question requires it
- **Summary only:** material conclusions may appear, but implementation-level detail is compressed

### Truth and permissions rule

Persona must not create a separate version of truth.

1. Permissions determine which evidence the user may access.
2. The question and relevance determine which evidence may answer the question.
3. Persona determines priority, depth, vocabulary, and presentation.

Relevant evidence should not be suppressed merely because it is unusual for the user’s role.

---

## 6. Enterprise knowledge layer

Use real platform names consistently:

- Salesforce
- Zoho CRM
- Zoho Desk
- SAP S/4HANA
- Google Drive
- Google Workspace
- Microsoft Azure
- Microsoft Entra ID
- Azure DevOps
- SharePoint
- Microsoft Teams
- GitHub
- Slack
- Jira
- Confluence
- ServiceNow
- Power BI

### Source identity treatment

Use a colored dot, source name, and record identifier instead of large logos.

Examples:

- `● Salesforce · Opportunity 0068Z00001`
- `● SAP · INV-900127`
- `● Zoho Desk · Ticket #4411`
- `● Google Drive · QBR Apr 2026 · Slide 14`
- `● GitHub · PR #482`
- `● Slack · #incident-acme`

### Source colors

| Source | Color |
|---|---|
| Salesforce | `#38BDF8` |
| SAP | `#F5B942` |
| Zoho | `#F87171` |
| Google Drive | `#4ADE80` |
| Microsoft / Azure | `#60A5FA` |
| GitHub | `#C084FC` |
| Slack | `#F472B6` |
| Jira / Confluence | `#818CF8` |
| ServiceNow | `#34D399` |
| Power BI | `#FACC15` |

The product must remain understandable without official brand logos.

---

## 7. Seven-stage journey

| Stage | UI label | User-visible meaning |
|---|---|---|
| 1 | **Question received** | The question and important entities were understood |
| 2 | **Audience understood** | The user’s role, perspective, and access were resolved |
| 3 | **Sources planned** | Relevant enterprise systems were selected |
| 4 | **Evidence gathered** | Authorized records and documents were collected |
| 5 | **Knowledge verified** | Facts, conflicts, and missing information were identified |
| 6 | **Answer built** | The facts were organized into a persona-appropriate narrative |
| 7 | **Visual brief composed** | The answer became panels, timelines, documents, and actions |

### Process visualization

Use a vertical rail with seven numbered nodes. Each node connects to a stage card.

Collapsed stage card:

- Stage number
- User-facing label
- One-line outcome
- Status: `Waiting`, `Working`, `Complete`, `Partial`, or `Needs attention`
- Duration for completed runs

Expanded stage card shows only information useful for comprehension. Never show prompts, chain-of-thought, credentials, or implementation code.

---

## 8. Experience architecture

Heimdall has two primary layers:

### Answer

The default view is a concise visual brief containing:

- User question
- One-sentence verdict
- Three to five visual panels
- Evidence chips attached to decision-relevant claims
- Visible conflict and information-gap indicators
- A short action path

### How it was built

A secondary view answers three questions:

1. What authorized sources were checked?
2. What facts, conflicts, and gaps were established?
3. How did those facts become the visible answer?

Recommended toggle:

`Answer | How it was built`

The process view is evidence, not an engineering console.

---

## 9. Global UI structure

### Header

**Left:** Heimdall wordmark and `Enterprise Intelligence`  
**Center:** Persistent question input  
**Right:** Persona selector and signed-in user chip

Input placeholder:

`Ask a question across your enterprise knowledge…`

Primary action:

`Build visual brief`

### Desktop canvas

- Artboard: `1440 × 1024`
- Maximum content width: `1280px`
- Outer margin: `48px`
- Twelve-column grid
- Column gap: `24px`
- Main result composition: six-column panels

The first mockup phase is desktop-first.

---

## 10. Required mockup frames

Create eight desktop frames.

### Frame 1 — Ask

- Heimdall header
- Signed-in user chip
- Large question field
- Three example questions
- Restrained row of enterprise sources
- Privacy line: `Heimdall only uses information you are permitted to access.`

Example questions:

- `Why did the Acme Corp renewal stall?`
- `What is blocking the Orion release?`
- `Summarize the customer risk before tomorrow’s QBR.`

### Frame 2 — Building the brief

- Question at the top
- Persona conclusion card
- Compact seven-stage progress indicator
- Current-stage card
- Source activity pills

Do not use a fake percentage. Show stage completion.

### Frame 3 — CxO answer

Question:

> Why did the Acme Corp renewal stall?

Verdict:

> **Acme’s renewal stalled on money and confidence: a ₹42L credit hold and three unresolved P1 incidents froze the ₹1.2Cr deal.**

Panels:

1. Hero KPI panel
2. SAP credit-hold document
3. Customer-confidence timeline
4. Missed SSO commitment
5. Recommended recovery path

### Frame 4 — CxO process

Show the seven-stage rail and:

- Authorized sources checked
- Sources skipped for relevance
- Sources unavailable by permission
- Key facts
- One conflict
- One information gap
- Mapping from facts to answer panels

### Frame 5 — Evidence drawer

Open from the right when an evidence chip is selected.

Example:

- Source: SAP S/4HANA
- Record: Customer invoice
- ID: INV-900127
- Customer: ACME CORP (100447)
- Amount: ₹42,00,000
- Due date: 1 May 2026
- Status: Credit hold active
- Claims supported
- Permission indicator
- Action: `Open in SAP`

### Frame 6 — Developer answer

User:

> **Maya Krishnan**  
> Senior Engineer · Platform Auth  
> **Developer view**

Verdict:

> **Acme’s SSO failure remained unresolved because the session fix in PR #482 waited 12 days for review while three P1 incidents stayed open.**

Panels:

1. Technical verdict
2. Incident timeline
3. Code diff
4. Jira delivery status
5. Remediation steps

Restricted commercial fields do not appear.

### Frame 7 — Developer process

Compared with the CxO view:

- GitHub, Slack, Jira, Azure DevOps, and Zoho Desk are prominent
- Salesforce is contextual
- SAP is unavailable or not selected
- Answer treatment is technical root cause
- Visuals use code diff and incident timeline instead of financial KPIs

### Frame 8 — Conflict / partial answer

Show:

- Salesforce says payment was received
- SAP says the invoice remains overdue
- Both source chips
- System-of-record explanation
- Verification action

Copy:

> **Records disagree**  
> A Salesforce note says payment was received, while SAP still reports INV-900127 as overdue with an active credit hold. SAP is treated as the billing system of record; Finance verification is recommended.

---

## 11. Answer components

### Verdict header

- Question label
- Large answer headline
- Highlighted key phrase
- Persona and source summary
- Generated time
- View toggle

### KPI tile

- Large value
- Short label
- Direction or state
- Evidence available on selection

### Source document panel

- Document or record preview
- Source and identifier
- Short interpretation
- Evidence chip
- `Open source` action

### Timeline

- Dates on one axis
- Events grouped by system
- Status markers
- Conflict markers
- Source chips attached to events

### Code-diff panel

- Monospace type
- Curated diff, not a full file
- Repository, pull request, file, status, owner, and age

### Action path

- Three to four numbered actions
- Owner
- Suggested timing
- Evidence basis
- Clear separation between fact and recommendation

### Evidence chip

Minimum content:

- Source-colored dot
- Source name
- Short record ID

Selecting an available chip opens the evidence drawer.

### Conflict chip

`⚠ Conflicts with Salesforce note · 12 May`

### Gap chip

`Gap · No executive sponsor activity since March`

Conflicts and gaps must sit near the claim they qualify.

---

## 12. Process-stage content

### Question received

- Original question
- Intent
- Account
- Topic
- Time window

### Audience understood

- User identity
- Role and department
- Persona
- Presentation lens
- Access summary

### Sources planned

Each source row shows:

- Platform
- Selection status
- Depth: `Deep`, `Standard`, `Context`, or `Not selected`
- Reason
- Permission state

`Unavailable by permission` and `Not selected for relevance` must be visibly different.

### Evidence gathered

- Record count by source
- Document and visual assets available
- Partial-source failures

### Knowledge verified

- Atomic fact
- Confidence
- Supporting sources
- Conflict block
- Gap block

Do not expose hidden model reasoning.

### Answer built

- Verdict
- Causes
- Risk
- Actions
- Evidence mapping
- Validation summary

### Visual brief composed

- Visual types selected
- Source assets reused
- Visuals computed from evidence
- Generated visuals, if any, clearly labeled

For the canonical demo, use zero decorative generated images.

---

## 13. Visual system

### Direction

The interface should feel like a calm enterprise intelligence room: serious, legible, evidence-led, and slightly cinematic.

It must not look like:

- A generic chatbot
- A CRM dashboard full of filters
- A developer observability console
- A fantasy game UI
- A slide deck embedded inside a browser

### Colors

| Token | Value | Use |
|---|---|---|
| Canvas | `#08111F` | Application background |
| Surface | `#13213A` | Primary cards |
| Raised surface | `#192A47` | Selected and expanded cards |
| Primary text | `#F7F9FC` | Headlines and values |
| Secondary text | `#DDE5F1` | Body |
| Muted text | `#91A0B7` | Metadata |
| Heimdall gold | `#E8B04A` | Primary action and active stage |
| Highlight gold | `#FFD481` | Verdict emphasis |
| Intelligence cyan | `#5BC0EB` | Evidence and focus |
| Success | `#54D18B` | Verified and healthy |
| Warning | `#F5B942` | Gaps and partial states |
| Risk | `#F06F6F` | Critical risk and conflicts |
| Purple | `#B491FF` | Engineering perspective |

### Typography

- Verdict and editorial headings: `Georgia` or `Source Serif 4`
- Product UI and body: `Inter`
- Data and code: `JetBrains Mono`

### Shape

- Main card radius: `16px`
- Small component radius: `10px`
- Pills: full radius
- Border: `1px` using white at approximately 8% opacity
- Avoid heavy drop shadows

### Motion

- Stage completion travels from 1 to 7
- Source pills appear as evidence is gathered
- Answer panels reveal in narrative order
- Persona switch cross-fades the entire brief
- Evidence drawer slides from the right

Motion explains state change; it does not imply invention.

---

## 14. Canonical demo data

**Company:** Vertex Gears  
**Customer:** Acme Corp  
**Question:** `Why did the Acme Corp renewal stall?`

### Users

| Persona | User | Role |
|---|---|---|
| Developer | Maya Krishnan | Senior Engineer · Platform Auth |
| Manager | Arjun Mehta | Engineering Manager · Identity Platform |
| Senior | Vikram Rao | Principal Architect · Enterprise Platforms |
| CxO | Priya Natarajan | VP Sales · Revenue · EMEA |

### Records

| Record | Source | Key information |
|---|---|---|
| Opportunity 0068Z00001 | Salesforce | Acme renewal · ₹1.2Cr · moved to Stalled on 14 May 2026 |
| Account note 0512 | Salesforce | Claims payment was received on 12 May |
| INV-900127 | SAP S/4HANA | ₹42L overdue · credit hold active from 2 May |
| Ticket #4411 | Zoho Desk | P1 · SSO login loop · open 34 days |
| Ticket #4415 | Zoho Desk | P1 · export failures · open 27 days |
| Ticket #4462 | Zoho Desk | P1 · API rate limits · open 22 days |
| Acme QBR Apr 2026, slide 14 | Google Drive | SSO GA promised by June 2026 |
| AUTH-291 | Jira | SSO epic · 68% complete |
| PR #482 | GitHub | Session fix · open 12 days awaiting review |
| #incident-acme | Slack | Team agrees PR #482 contains the likely fix |
| CSAT series | Zoho CRM | CSAT declined from 4.6 to 2.1 |

### Intentional conflict

Salesforce says payment was received; SAP says the invoice remains overdue.

### Intentional gap

No executive-sponsor activity is recorded after March.

---

## 15. Interaction states

### Asking

1. Enter question.
2. Select `Build visual brief`.
3. Show building state.
4. Progress through seven stages.
5. Reveal answer.

### Switching persona

One selection updates:

- Signed-in demo user
- Persona
- Source plan
- Headline
- Panel order
- Visual types
- Evidence available
- Process explanations

CxO and Developer require complete mockups. Manager and Senior may remain visible but disabled during the first prototype.

### Partial result

Useful evidence should survive a source failure.

Example:

> `Partial brief · ServiceNow was unavailable. The answer uses 4 of 5 planned sources.`

Do not replace a useful partial result with a generic error screen.

---

## 16. What the UI reveals and protects

### Reveal

- User question
- Concluded persona
- Authorized sources
- Relevance skips
- Permission skips
- Gathered evidence
- Verified facts
- Conflicts
- Information gaps
- Fact-to-panel mappings

### Protect

- System prompts
- Chain-of-thought
- Raw retrieval queries
- Persona-weight numbers
- Internal JSON schemas
- Model settings
- Credentials
- Tokens
- Connector implementation

Trust comes from evidence and outcomes, not disclosure of proprietary orchestration.

---

## 17. Accessibility

- Minimum normal-text contrast: `4.5:1`
- Do not communicate status through color alone
- Evidence chips require keyboard focus
- Interactive targets should be at least `40px` high where practical
- Icons need text labels
- Critical evidence cannot exist only on hover
- Timelines and charts need text summaries
- Risk and success colors require labels or icons

---

## 18. Mockup acceptance criteria

The mock-design phase is complete when:

1. All eight required desktop frames exist.
2. CxO and Developer answers visibly differ in content, sources, and visual vocabulary.
3. User identity and persona are always clear.
4. Source priority changes with persona without implying that persona changes truth.
5. All seven stages are understandable without technical explanation.
6. Every decision-relevant answer panel has inspectable evidence.
7. The evidence drawer is fully designed.
8. Permission skips, relevance skips, conflicts, and gaps are visibly distinct.
9. Real enterprise platform names are used consistently.
10. The CxO answer is understandable within ten seconds.
11. The process view proves trust without exposing prompts or hidden reasoning.
12. The screens support a ninety-second demo without requiring narration to explain basic behavior.

---

## 19. Design decision hierarchy

When choices conflict, use this order:

1. Make the answer immediately understandable.
2. Make the evidence easy to inspect.
3. Make persona adaptation unmistakable.
4. Make uncertainty honest.
5. Make the seven-stage journey clear.
6. Add visual polish.

The interface has failed if it looks sophisticated but the user cannot quickly tell what happened, why it happened, and which evidence supports the conclusion.