# Heimdall — UI and Product Design Specification

**Purpose:** Source of truth for creating the Heimdall mockup UI  
**Current phase:** Mock-design refinement  
**Next phase:** Clickable prototype

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

Create the compact Developer mobile flow first, then expand the approved information hierarchy to desktop and the other personas. The mock should prove the idea without requiring a working backend.

### Phase 3 — Prototype

Replace mock data and simulated transitions with a working pipeline. The prototype implements the approved mock rather than redesigning the product during development.

### Approved direction from the minimal UI exploration

The supplied minimal UI exploration establishes the preferred interaction direction:

- Question-first, not dashboard-first
- One-sentence answer before supporting detail
- Progressive disclosure instead of showing every panel at once
- Mobile flow as the fastest way to prove the core idea
- Details open inline or on a focused pushed screen
- Process is available for trust, but never competes with the answer
- No fake percentage progress

The exploration is a structural reference, not a pixel-perfect final design. It contains legacy `Drishti` naming, a generic red-accent design system, and unproven claims about determinism and runtimes. Those elements are not approved.

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
- Measured duration for completed prototype runs; omit it in static mockups

Expanded stage card shows only information useful for comprehension. Never show prompts, chain-of-thought, credentials, or implementation code.

---

## 8. Experience architecture

Heimdall has two primary layers:

### Answer

The default view is a concise visual brief containing:

- User question
- One-sentence verdict
- Source count, evidence status, and generated time
- Four or five collapsed topic rows
- Evidence chips attached to decision-relevant claims
- Visible conflict and information-gap indicators
- A follow-up input

For the Developer flow, use these rows in this order:

1. **Evidence** — record and source count
2. **Likely fix** — pull request, file, or technical conclusion
3. **Incident timeline** — the events that establish causality
4. **Recommended actions** — owners, sequence, and timing
5. **How this was built** — seven stages and source-selection outcomes

Only the one-sentence verdict is expanded by default. Selecting a topic may expand it inline for a quick scan or push to a focused detail screen when the content needs code, records, or a longer timeline.

Do not use chat bubbles. Heimdall is question-first and answer-first, but it is not presented as a conversation transcript.

### How it was built

A secondary view answers three questions:

1. What authorized sources were checked?
2. What facts, conflicts, and gaps were established?
3. How did those facts become the visible answer?

On desktop, use `Answer | How it was built` as a view toggle.

On mobile, place **How this was built** as the final collapsed topic row. This keeps process available without making it a primary navigation decision.

The process view is evidence, not an engineering console.

### Progressive-disclosure rule

At every screen depth, reveal only what helps the user make the next decision:

| Level | Show | Keep behind interaction |
|---|---|---|
| Answer | Verdict, strongest metric or fact, topic rows | Full records, code, stage detail |
| Expanded row | Short summary, source chips, one next action | Complete record and external system |
| Detail screen | Full supporting view and permission context | Internal orchestration |
| External system | Original authorized record | Heimdall internals |

The UI should feel simpler as the underlying evidence becomes more complex.

---

## 9. Global UI structure

### Mobile header

**Left:** Back control when needed, compact Heimdall avatar, `HEIMDALL`  
**Right:** Signed-in user and concluded persona, for example `Maya K. · Developer`

The header is deliberately small. The mythological avatar may be `28px` in the header and up to `96px` on the empty Ask screen. Do not repeat the large guardian visual inside answer and evidence screens.

### Question input

Ask-screen placeholder:

`Ask a question across your enterprise knowledge…`

Follow-up placeholder:

`Ask a follow-up…`

The submit control may be an icon button when its accessible name is available.

### Mobile canvas

- Reference content width: `402px`
- Reference artboard: `402 × 874`
- Side padding: `16px`
- Major vertical spacing: `16–24px`
- Minimum interactive target: `44px`
- One-column composition
- Sticky follow-up input on answer screens
- No permanent bottom navigation in the first prototype

The first clickable prototype is mobile-first because it forces a clear hierarchy and is easier to demonstrate as one continuous flow.

### Desktop canvas

- Artboard: `1440 × 1024`
- Maximum content width: `1280px`
- Outer margin: `48px`
- Twelve-column grid
- Column gap: `24px`
- Main result composition: answer column plus optional evidence or process column

Desktop adapts the approved mobile hierarchy; it must not introduce a separate information architecture.

---

## 10. Required mockup frames

### Core mobile flow — build first

Create these seven connected frames:

1. **Ask** — avatar, product promise, example questions, Developer lens, connected-source count, question input, permission line
2. **Building** — question, current named stage, `stage N of 7`, collapsed stage list, source activity
3. **Answer** — one-sentence verdict and five collapsed topic rows
4. **Likely fix detail** — repository, file, review state, compact diff, source chips, `Open in GitHub`
5. **Evidence detail** — record counts grouped by source, unavailable-by-permission state, permission reminder
6. **Timeline and actions** — causal events followed by clearly labeled recommendations
7. **How this was built / honest states** — seven stages, sources used/skipped/unavailable, conflict, gap, and partial-result treatment

Navigation contract:

`Ask → Building → Answer → Detail → Back to Answer`

Back from Building returns to Ask. Back from a detail screen returns to the same answer state. A follow-up begins a new run while preserving the previous question in history.

### Desktop expansion — build after the mobile flow

Create eight desktop frames using the same hierarchy.

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

The interface should feel like a precise enterprise briefing: quiet, editorial, evidence-led, and fast to scan.

Use the minimal UI exploration’s flat structure, strong rules, compact metadata, and progressive disclosure. Keep Heimdall’s navy-and-gold identity instead of inheriting the exploration’s generic red accent.

It must not look like:

- A generic chatbot
- A CRM dashboard full of filters
- A developer observability console
- A fantasy game UI
- A slide deck embedded inside a browser
- A grid of equally important cards
- A dark cinematic interface that reduces legibility during a live demo

### Colors

| Token | Value | Use |
|---|---|---|
| Canvas | `#F3F2F2` | Application background |
| Surface | `#FFFFFF` | Answer and detail surfaces |
| Muted surface | `#EAE9E9` | Inputs and secondary regions |
| Primary text | `#201E1D` | Headlines, values, and body |
| Muted text | `#696563` | Metadata; chosen for readable contrast |
| Divider | `rgba(32, 30, 29, 0.28)` | Rules and boundaries |
| Heimdall navy | `#081A33` | Avatar, wordmark, and high-emphasis text |
| Action gold | `#9A6200` | Primary action, focus, and active stage |
| Gold tint | `#F4E4C4` | Selected and highlighted background |
| Success | `#287A50` | Verified and healthy |
| Warning | `#9A6200` | Gaps and partial states |
| Risk | `#B42318` | Critical risk and conflicts |

Platform colors identify source provenance only. They do not compete with status colors or the primary action.

### Typography

- Product headings and body: `Archivo`
- Data and code: `JetBrains Mono`
- System fallback: `system-ui, sans-serif`

Use weight and spacing before adding more colors. The one-sentence verdict is the largest text on the Answer screen.

### Shape

- Main surfaces: square or `2px` radius
- Source chips: square or `2px` radius
- Use `1px` and `2px` dividers to create hierarchy
- Avoid floating-card shadows
- Reserve circles for the avatar, status dots, and source marks

The interface should be organized by spacing and rules, not by nesting many rounded containers.

### Motion

- Stage completion travels from 1 to 7
- Source pills appear as evidence is gathered
- Answer rows reveal in narrative order
- Inline details open without moving the user away from context
- Pushed detail screens use a short horizontal transition
- Persona switch cross-fades the answer content

Motion explains state change; it does not imply invention.

Use approximately `150–250ms` for interface transitions. Respect reduced-motion preferences. Do not animate the guardian’s eyes.

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
2. Submit with the arrow action or select a suggested question.
3. Show building state.
4. Progress through seven stages.
5. Reveal answer.

### Building

- Show the current named stage and `stage N of 7`
- Keep the complete stage list collapsed by default
- Reveal source activity only after evidence gathering begins
- Use `Working`, `Found`, `Unavailable`, and `Complete`; do not simulate precision
- Allow Back to return to Ask

### Inspecting the answer

- Tapping a collapsed row expands a short preview or opens a detail screen
- Tapping a source chip opens the evidence record with its permission context
- Back returns to the same answer and scroll position
- External-system actions use explicit labels such as `Open in GitHub`
- Recommendations remain visually and verbally distinct from established facts

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

### Claims the interface may make

Use trust language only when the prototype can support it:

| Claim | Requirement |
|---|---|
| `Every claim linked` | Every visible factual claim has an inspectable evidence mapping |
| `N sources connected` | The count reflects authenticated connectors available to this user |
| `N records from M sources` | The evidence detail lists those exact records and sources |
| `Partial brief` | Missing sources and the effect on the answer are named |
| `Reproducible run` | The system records the question, permission snapshot, source versions, and configuration needed to reproduce it |
| `Deterministic run` | Avoid this claim unless repeated controlled tests produce the same result |

Do not present invented stage durations such as `15.3s` in a working prototype. During static mockups, omit runtimes or label the entire screen as demo data. A judge is more likely to trust an honest stage indicator than fabricated precision.

---

## 17. Accessibility

- Minimum normal-text contrast: `4.5:1`
- Do not communicate status through color alone
- Evidence chips require keyboard focus
- Interactive targets should be at least `44px` high where practical
- Icons need text labels
- Critical evidence cannot exist only on hover
- Timelines and charts need text summaries
- Risk and success colors require labels or icons

---

## 18. Mockup acceptance criteria

The mock-design phase is complete when:

1. The seven mobile frames form a connected Ask → Build → Answer → Detail flow.
2. The default Answer screen is one sentence plus no more than five collapsed topic rows.
3. Back navigation returns to the expected state without losing the answer.
4. User identity and persona are always clear.
5. The UI uses `Heimdall` everywhere; no `Drishti` label remains.
6. All seven stages are understandable without technical explanation or fake percentage progress.
7. Every decision-relevant claim has inspectable evidence.
8. Permission skips, relevance skips, conflicts, gaps, and recommendations are visibly distinct.
9. Real enterprise platform names are used consistently.
10. No unproven deterministic or precise-runtime claim appears.
11. The process view proves trust without exposing prompts or hidden reasoning.
12. The Developer answer is understandable within ten seconds.
13. The mobile screens support a ninety-second demo without narration to explain basic behavior.
14. The later CxO and Developer desktop answers visibly differ in content, sources, and visual vocabulary while preserving the same interaction hierarchy.

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
