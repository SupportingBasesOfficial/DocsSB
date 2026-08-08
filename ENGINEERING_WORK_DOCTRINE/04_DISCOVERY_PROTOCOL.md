# DISCOVERY PROTOCOL (GREENFIELD)

## Purpose of This File

This file defines the official **greenfield discovery protocol** (for new projects) of the Engineering Work Doctrine.

> **Cross-reference:** Before conducting discovery, classify the work request using `11_TASK_CLASSIFICATION_GUIDE.md`. This protocol applies when the work is classified as a **Project** (greenfield). For discovery of existing systems (brownfield), see `15_BROWNFIELD_DISCOVERY_PROTOCOL.md`.

> **Proportionality Note:** Discovery depth scales with work type per the Proportionality Principle. This protocol describes the full discovery depth for new projects. For features, refactoring, bugfixes, tasks, and questions, discovery depth is reduced proportionally — see the relevant lifecycle path in `03_PROJECT_LIFECYCLE.md`.

> **Operational State Note:** Discovery depth also scales with Operational State. In Stable state, full discovery is required. In Formative state, discovery may be lighter (the work is still being shaped). In Exploratory state, discovery is minimal or skipped (the output is throwaway). See `21_OPERATIONAL_STATES.md`.

> **Mega-tech Discovery:** In Stable state, discovery must also surface the mega-tech dimensions (security, observability, data governance, testing, dependencies) per `22_DISCOVERY_DIMENSION_PROTOCOL.md` Categories 9-13. These dimensions ensure that production-grade work understands its mega-tech landscape before construction begins.

Discovery is the first formal operational phase of the doctrine for new projects.

Its role is to transform a raw project impulse into structured, interpretable, decision-ready material without requiring the user to already think like an architect, product strategist, systems analyst, or infrastructure designer.

This is the greenfield discovery protocol — it applies when a new project is being initiated from scratch.

This file exists to ensure that discovery:
- is not improvised
- is not vague
- is not dependent on user technical fluency
- does not prematurely collapse into solution design
- does not fail to surface hidden structural dimensions
- produces enough clarity to support deterministic consolidation

Discovery is not casual conversation.  
Discovery is controlled emergence of project meaning.

---

## Role of Discovery in the Doctrine

Under this doctrine, discovery exists between:
- raw project impulse
- and deterministic consolidation

It is the phase in which the AI must:
- interpret the user's intent
- expand awareness responsibly
- expose relevant decision domains
- clarify what matters structurally
- reduce ambiguity
- identify hidden implications
- make the project legible before formal contracting

Discovery is not the place to begin serious build output.

Discovery is the place to reveal what the project actually is.

---

## Core Objective of Discovery

The core objective of discovery is to answer this question:

**What does this project need to become, in structural terms, before serious construction can responsibly begin?**

This requires the AI to uncover:
- identity
- purpose
- operational nature
- actors
- workflows
- data implications
- control needs
- risk dimensions
- experience expectations
- growth implications
- constraints
- unknowns
- future-relevant structural dimensions

Discovery succeeds when the project stops being merely desired and starts becoming structurally interpretable.

---

## Discovery Principles

The discovery phase must obey the following principles.

### 1. Discovery Must Be Guided
The AI must lead discovery actively.

The user must not be forced to invent the entire structure of the clarification process.

### 2. Discovery Must Be Accessible
The language must remain understandable to a non-specialist user.

### 3. Discovery Must Reduce Ambiguity
Questions must be designed to make the project clearer, not merely longer.

### 4. Discovery Must Surface Structure
The AI must reveal dimensions the user may not have considered.

### 5. Discovery Must Not Inflate Scope
The AI may broaden awareness, but must not smuggle optional sophistication into confirmed need.

### 6. Discovery Must Not Become Delivery
Discovery is not the stage for serious architecture, deep technical commitment, or implementation artifacts.

### 7. Discovery Must Produce Consolidatable Material
The output of discovery must be structured enough to support deterministic consolidation.

---

## Discovery Entry Condition

Discovery begins when the project exists as a raw impulse but is not yet sufficiently structured for consolidation or delivery.

Typical signals that discovery should begin:

- the user expresses a project idea but not its shape
- the user describes pain but not system structure
- the user asks for a project without enough operational detail
- the user has ambition but not clarified dimensions
- the user wants a system, app, platform, or workflow but has not yet articulated its actors, flows, controls, or constraints
- the user clearly needs help discovering what to ask for

If the project is already exceptionally well-defined, discovery may be shortened, but its logic may not be skipped silently.

---

## Discovery Exit Condition

Discovery ends only when the AI has enough structured understanding to support deterministic consolidation.

This means discovery must have produced material sufficiently clear to answer, at minimum:

- what the project fundamentally is
- who it serves
- what kind of operational reality it must support
- what primary flows exist
- what control or permission layers matter
- what data or records matter
- what main constraints exist
- what major unknowns remain
- what plausible horizon differs from confirmed scope
- what structural implications have already emerged

If these are still too vague, discovery is not complete.

---

## Official Discovery Responsibilities of the AI

During discovery, the AI is responsible for all of the following:

### 1. Interpret the Raw Impulse
Understand what the user is pointing toward, even if the wording is incomplete or non-technical.

### 2. Visualize the Maximum Plausible Horizon
Internally consider what the project could realistically become if it grows in significance.

### 3. Identify Relevant Discovery Domains
Select which project dimensions need clarification based on the type of project being discussed.

### 4. Translate Complexity into Accessible Decision Blocks
Turn technical implications into user-answerable decisions.

### 5. Reveal Structurally Relevant Possibilities
Surface dimensions the user may not have anticipated, without forcing them into confirmed scope.

### 6. Classify Emerging Ambiguity
Detect where information is clear, partial, missing, critical blocking, important non-blocking, or evolutive.

### 7. Protect Against Premature Build Thinking
Prevent the conversation from collapsing into architecture or implementation before discovery is mature enough.

### 8. Prepare the Ground for Consolidation
Ensure the discovery outputs are coherent enough to become the basis for a work agreement.

---

## What Discovery Must Clarify

Discovery should clarify, as applicable to the project, the following categories.

### A. Essence of the Project
- What kind of thing is this?
- What is it fundamentally trying to do?
- What transformation or outcome matters?

### B. Operational Nature
- Is this an app, internal system, platform, workflow tool, SaaS, offline environment, automation layer, operational dashboard, control system, hybrid product, or something else?
- What kind of operational class does it belong to?

### C. Users and Actors
- Who uses it?
- Who operates it?
- Who administers it?
- Who only views?
- Who decides?
- Who controls permissions?

### D. Core Flows
- What must happen from beginning to end?
- What repeated workflows define the system?
- What events matter?

### E. Data and Records
- What needs to be stored?
- What needs to be retrieved?
- What needs to be auditable?
- What must remain traceable?

### F. Control and Governance
- What permissions matter?
- What should be restricted?
- What needs approval?
- What should be logged?
- What must remain reversible or non-reversible?

### G. Experience Expectations
- What experience should it feel like?
- Should it be simple, fast, operational, elegant, technical, mobile-first, desktop-first, offline-capable, highly guided, minimal-friction, or deeply controlled?

### H. Automation and Intelligence
- What could be automated?
- What should be suggested?
- What alerts may matter?
- What intelligence layers could support users?

### I. Reliability and Safety
- What could go wrong operationally?
- What demands traceability?
- What demands auditability?
- What demands resilience, consistency, or protection?

### J. Scale and Evolution
- Could it grow into multi-user, multi-unit, multi-company, platform, product, or integrated system form?
- What dimensions may become important later?

### K. Constraints
- What devices matter?
- What connectivity constraints exist?
- What time, money, skill, deployment, environment, or ownership constraints matter?

### L. Unknowns
- What is still undefined?
- What must be clarified before build?
- What may safely remain an evolutive lacuna?

Not every project requires equal depth in every category.  
The AI must adapt discovery to relevance.

---

## Discovery Structure Model

The doctrine recommends discovery through structured blocks rather than freeform interrogation.

The ideal discovery structure is block-based.

A typical discovery sequence may look like:

1. Project essence
2. Users and actors
3. Operational flows
4. Records and data
5. Control and permissions
6. Experience expectations
7. Automation and intelligence
8. Reliability and governance
9. Scale and future evolution
10. Constraints and environment
11. Open uncertainties

This order may vary, but the AI must keep discovery structured enough for later consolidation.

---

## Preferred Response Formats During Discovery

Whenever possible, discovery should use response formats that reduce cognitive friction.

Preferred formats include:

- Yes / No / Maybe / Not Sure / Observation
- Multiple choice
- Short tagged options
- Priority ranking
- Simple comparative choices
- Short operational explanation fields
- Guided scenario selection

Discovery should avoid overdependence on:
- long blank-form responses
- expert language requirements
- architecture-first framing
- stack-first framing
- abstract jargon without explanation

The user should feel guided, not examined.

---

## How Questions Must Be Written

Doctrine-compliant discovery questions must be written in a way that is:

- accessible
- brief enough to answer
- explicit about what is being decided
- structurally meaningful
- low-friction
- non-patronizing
- semantically precise

A good discovery question does three things:
1. names the decision area
2. explains why it matters in simple terms
3. provides an easy way to answer

### Example of Weak Question
“Do you need RBAC?”

### Example of Strong Question
“Will different people using this system need different levels of access, such as admin, operator, viewer, manager, or restricted user?  
Mark: Yes / No / Maybe / Not Sure / Observation”

The doctrine favors the second form.

---

## Discovery Must Reveal Without Forcing

The AI must reveal possible dimensions the user may not yet see.

For example, it may surface:
- audit history
- user roles
- approval steps
- offline operation
- multi-unit structure
- synchronization needs
- export layers
- dashboard layers
- automation rules
- alerting needs
- traceability
- ownership and environment boundaries

However, the AI must present these as:
- relevant clarifications
- strategic possibilities
- structural implications

It must not present them as mandatory scope unless confirmed.

The AI expands awareness, but does not hijack the project.

---

## Discovery and Horizon Awareness

During discovery, the AI must internally distinguish between:

### Maximum Plausible Horizon
What the project could become if its importance or scale grows.

### Structural Initiation Needs
What the project must consider from the start to avoid irresponsible initiation.

### Present Confirmed Need
What the user actually confirms as needed now.

The AI may use horizon awareness to shape better questions, but must not confuse horizon with present scope.

This separation is mandatory during discovery.

---

## What Discovery Must Not Do

Discovery must not:

- prematurely finalize the architecture
- commit to a stack without enough basis
- produce deep implementation plans
- confuse possibility with confirmation
- overinflate the project
- underinvestigate critical dimensions
- silently assume unclear structural needs
- present build artifacts as though the project were already ready
- turn into a showcase of AI cleverness
- exhaust the user with unnecessary questioning

Discovery must remain disciplined, not theatrical.

---

## Ambiguity Handling During Discovery

When uncertainty appears, the AI must not ignore it.

The AI must:
- surface it
- frame it clearly
- decide whether it needs immediate clarification
- classify whether it is a critical blocking lacuna, an important non-blocking lacuna, or an evolutive lacuna
- avoid pretending that it has been resolved when it has not

Discovery is one of the main places where ambiguities should first become visible.

The AI must prefer:
- visible uncertainty
- over silent distortion

---

## Discovery Depth Calibration

Not all projects require the same discovery depth.

The AI must calibrate discovery based on:

- project complexity
- operational weight
- number of actors
- governance sensitivity
- safety implications
- business criticality
- platform ambition
- offline/online complexity
- data seriousness
- integration surface
- scope volatility
- user uncertainty level

A small internal tool and a multi-tenant operational platform do not require identical discovery depth.

However, even simpler projects must still be initiated with structural seriousness.

The doctrine does not allow discovery to become shallow just because the project seems small.

It requires proportional depth.

---

## Discovery Completion Test

Before ending discovery, the AI should be able to answer:

- Do I understand what this project fundamentally is?
- Do I understand who it serves?
- Do I understand what the most important flows are?
- Do I understand what must be controlled, stored, or protected?
- Do I understand the main operational constraints?
- Have I surfaced major structural dimensions that the user may not have considered?
- Can I clearly distinguish confirmed scope from plausible horizon?
- Are the remaining lacunae visible and classifiable?
- Is the material now structured enough to consolidate?

If the answer is no to too many of these, discovery is incomplete.

---

## Discovery Outputs

A correct discovery phase should produce material that is ready to be consolidated into:

- clarified project identity
- actor map
- operational flow understanding
- control and governance implications
- data implications
- experience expectations
- constraints map
- scale implications
- lacuna map
- distinction between confirmed and possible
- preliminary structural implications

These are not yet the final contract.  
They are the raw structured outputs required for consolidation.

---

## Discovery Failure Modes

Discovery has failed when any of the following happen:

- the AI asks many questions but reveals little structure
- the user is forced into technical language to continue
- the AI begins designing before the project is understood
- hidden dimensions remain hidden because they were never surfaced
- ambiguity is silently absorbed instead of handled
- the discovery becomes exhausting rather than clarifying
- the AI expands into unnecessary complexity without need
- the outputs remain too fragmented for consolidation
- scope and horizon become confused
- the project appears clearer than it really is

These are doctrinal discovery failures.

---

## Discovery Success Condition

Discovery is successful when:

- the project is no longer just an idea
- the user has been guided without needing specialist vocabulary
- key dimensions have been surfaced
- ambiguity has been reduced and classified
- relevant possibilities have been revealed responsibly
- confirmed present needs are distinguishable from plausible future evolution
- the outputs are coherent enough to support deterministic consolidation

That is the official success condition of discovery.

---

## Next File

Continue to:

`05_CONSOLIDATION_PROTOCOL.md`