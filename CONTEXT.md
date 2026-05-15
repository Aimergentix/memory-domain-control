# Memory Domain Control

This context defines the canonical language for authoring a local-first agent protocol and its public framing. It exists to keep naming, scope, and claims stable across gist drafts.

## Language

**Memory Domain Control**:
The operating discipline for explicit, domain-scoped agent state and policy-gated memory.
_Avoid_: Harness, chat mode, memory purge

**Memory Domain Protocol (MDP)**:
The canonical public name for the copy-paste prompt and runtime contract that instantiates Memory Domain Control in a model session.
_Avoid_: Template, prompt trick, setup note

**Domain**:
A bounded work context that groups related assumptions, constraints, and state around one objective.
_Avoid_: global memory pool, user identity, arbitrary label

**Protocol-first**:
A framing where the asset is presented as an operating protocol, with memory hygiene as one subsystem rather than the whole product.
_Avoid_: Memory-first, persona-first, architect mode

**Two-layer standard**:
A framing where the public asset includes both an immediately usable Master System Prompt and a runtime implementation contract that carries the real enforcement guarantees.
_Avoid_: Prompt-only standard, magic prompt

**Role-neutral core**:
A protocol baseline that avoids tying the standard to a specific operator identity, seniority, or tone.
_Avoid_: Persona-bound core, elite-only prompt

**Architect Profile**:
An optional operator profile that applies senior-peer tone, higher signal density, and stricter stylistic constraints on top of the role-neutral core.
_Avoid_: Default persona, required identity

**Control tokens**:
The public-facing prompt interface for selecting a single MDP operation such as `#transform`, `#refactor`, `#intent`, or `#summarize`.
_Avoid_: KDBT, magic hashtags

**Composite control token**:
A primary control token that emits multiple coordinated artifacts in one deterministic output contract rather than performing a single narrow transformation.
_Avoid_: vague catch-all state, alias-only token

**Execution state**:
The runtime state entered after parsing a control token and resolving turn-local constraints.
_Avoid_: mode soup, chat behavior

**State contamination**:
The primary failure mode where assumptions, preferences, or task state leak across boundaries and distort the current run.
_Avoid_: prompt drift, model stupidity

**Contextual bleed**:
The user-facing name for state contamination when memory or prior context leaks into an unrelated task.
_Avoid_: forgetfulness, randomness

**Constraint Modularization**:
The core MDP mechanism that separates TASK requirements from ENVIRONMENT requirements so execution stays inspectable and portable.
_Avoid_: hidden assumptions, mixed constraints

**Visible constraint split**:
An explicit `TASK` and `ENVIRONMENT` section emitted in the output of every non-standard primary control token.
_Avoid_: implicit assumptions, hidden environment state

**Semantic Delta**:
An optional overlay that proposes more precise operator vocabulary after a transformation.
_Avoid_: required protocol behavior, default output tax

**Token Metrics**:
An optional overlay that estimates compression or expansion between source input and transformed output.
_Avoid_: fake precision, mandatory telemetry

**GDPR Ready**:
A public badge phrase indicating engineering alignment with data minimization, local-first operation, and explicit operator control, not legal certification.
_Avoid_: certified compliant, legal guarantee

**Dual interface**:
A two-surface protocol design where human operators use control tokens and runtimes use explicit state mutators.
_Avoid_: single-surface prompt, hidden runtime contract

**State mutators**:
Machine-parseable commands such as `STATE_ADD`, `STATE_MOD`, and `STATE_DEL` that perform explicit state transactions in the implementation layer.
_Avoid_: conversational memory edits, implicit state writes

**CLI-like DSL**:
The canonical public syntax for MDP state mutators, using command-style verbs and flags that are legible to operators and easy to parse in runtimes.
_Avoid_: JSON-only contract, hidden schema

**Two-line title stack**:
A public heading structure where the formal standard name appears first and a broader marketing subtitle carries the SEO and hook value.
_Avoid_: single hype title, title overload

**Platform-neutral language**:
Protocol wording that avoids tying the standard to Unix, POSIX, Linux, or any other platform-specific metaphor set.
_Avoid_: Linux-only framing, platform doctrine

**Scoped override**:
A turn-local `#constraint:[...]` behavior that overrides only conflicting baseline rules while preserving all non-conflicting protocol defaults.
_Avoid_: full baseline replacement, constraint wipe

**Portable session bootstrap artifact**:
The canonical `#summarize` output: an operator-owned handoff artifact for reuse in later sessions without being treated as the baseline system prompt.
_Avoid_: replacement system prompt, narrative recap

**Runtime Contract section**:
A visible main-body section of the gist that presents the canonical `STATE_*` interface, while transport-specific mappings such as JSON stay inside advanced details.
_Avoid_: hidden runtime layer, prompt-only framing

**Local-First: Validated**:
A public badge phrase indicating that MDP has been engineered against a local-first reference pattern with operator-owned state, no assumed cloud memory, and explicit persistence boundaries.
_Avoid_: third-party certification, undefined claim

**Protocol acknowledgment tokens**:
The canonical short-form runtime replies for `STATE_*` operations, such as `STATE_OK`, `STATE_ERR_INVALID`, and `STATE_ERR_POLICY`.
_Avoid_: bracketed prose acknowledgments, verbose status text

**STATE_ERR_NOT_FOUND**:
The canonical runtime reply when a referenced domain, node, or target does not exist.
_Avoid_: overloading invalid syntax errors, silent misses

**Inspection response shape**:
The canonical response pattern for inspection commands: a status token on the first line followed by a structured payload on subsequent lines.
_Avoid_: payload-only reads, unstructured prose dumps

**Canonical JSON payload**:
The standard structured payload format for inspection responses in MDP, emitted after the status token.
_Avoid_: ad hoc read payloads, prose-only inspection output

**Error response shape**:
The canonical response pattern for runtime errors: an error token on the first line followed by a compact JSON payload describing the failure.
_Avoid_: token-only opaque errors, prose-only failures

**Mutation response shape**:
The canonical response pattern for successful mutation commands: `STATE_OK` on the first line followed by a compact JSON payload confirming the operation and affected identifiers.
_Avoid_: token-only success replies, ambiguous mutation confirmation

**Task Profiles**:
Optional behavior bundles layered on top of MDP for specific work types such as code review or architecture critique, published inside advanced details rather than the core standard.
_Avoid_: protocol core behavior, mandatory workflow bundle

**Single primary control token**:
An MDP routing invariant where exactly one primary control token may appear per turn; if multiple appear, the operator must choose one before execution continues.
_Avoid_: stacked primary tokens, hidden precedence

**Explicit domain scoping**:
A core MDP invariant requiring state operations and scoped retrieval to name or resolve a domain explicitly rather than relying on implicit cross-domain memory.
_Avoid_: global memory pool, implicit cross-domain access

**Active domain**:
The currently selected domain used as the default retrieval boundary for the current session or execution context.
_Avoid_: ambient context, inferred global scope

**Hybrid domain model**:
An MDP runtime model where retrieval defaults to one **Active domain**, writes remain explicitly scoped, and cross-domain access must always be opt-in.
_Avoid_: fully implicit routing, global default memory

**STATE_USE**:
The canonical runtime command for selecting the **Active domain** using the form `STATE_USE --domain <name>`.
_Avoid_: ad hoc domain switching, implicit activation

**Explicit node identifier**:
A required `--id` value on `STATE_ADD` so later `STATE_MOD` and `STATE_DEL` operations can target stable, operator-chosen nodes.
_Avoid_: runtime-generated opaque IDs, anonymous state entries

**Global node identifier**:
A node identifier that is unique across all domains, allowing direct node targeting without requiring domain-qualified lookup.
_Avoid_: per-domain duplicate IDs, ambiguous targets

**Explicit scoped reference**:
A reference that counts as explicit scope in MDP, either by naming a domain directly or by naming a globally unique node identifier.
_Avoid_: ambient scope, hidden cross-domain lookup

**STATE_DROP**:
The canonical runtime command for deleting an entire domain using the form `STATE_DROP --domain <name>`.
_Avoid_: overloading node deletion, implicit destructive scope removal

**STATE_INIT**:
The canonical runtime command for explicit domain creation using the form `STATE_INIT --domain <name>`.
_Avoid_: implicit domain creation, accidental domains from typos

**Inspection commands**:
Explicit runtime commands for reading or inspecting state rather than relying only on implicit retrieval through the active domain.
_Avoid_: write-only protocol, hidden inspection path

**STATE_LIST**:
The canonical runtime command for enumerating available domains or the contents of a named domain, always with an explicit selector such as `--domains` or `--domain <name>`.
_Avoid_: overloaded read verbs, implicit listing

**STATE_GET**:
The canonical runtime command for inspecting one state node by target identifier.
_Avoid_: overloaded read verbs, ambiguous target lookup

## Relationships

- **Memory Domain Control** is implemented through the **Memory Domain Protocol (MDP)**
- A **Domain** is the primary state boundary inside **Memory Domain Control**
- **Protocol-first** positions the **Memory Domain Protocol (MDP)** as the primary artifact
- **Two-layer standard** lets the **Memory Domain Protocol (MDP)** deliver immediate prompt value without overstating prompt-only guarantees
- The **Role-neutral core** makes the **Memory Domain Protocol (MDP)** broadly reusable
- The **Architect Profile** is an optional overlay on the **Role-neutral core**
- **Control tokens** select an **Execution state**
- `#transform` is the **Composite control token** in the public control surface
- **Contextual bleed** is the common symptom of **State contamination**
- The **Memory Domain Protocol (MDP)** exists primarily to reduce **State contamination**
- **Constraint Modularization** belongs to the MDP core
- Every non-standard primary control token emits a **Visible constraint split**
- **Semantic Delta** and **Token Metrics** are optional overlays, not core protocol requirements
- **GDPR Ready** is a trust signal about engineering posture, not a legal claim
- The **Dual interface** pairs **Control tokens** for operators with **State mutators** for runtimes
- The **CLI-like DSL** is the canonical syntax for **State mutators**
- The **Two-line title stack** pairs the formal MDP name with a broader mission-control subtitle
- The **Role-neutral core** should also use **Platform-neutral language**
- `#constraint:[...]` should act as a **Scoped override**
- `#summarize` should emit a **Portable session bootstrap artifact**
- The visible **Runtime Contract section** should present the `STATE_*` interface in the main body
- **Local-First: Validated** means engineering validation against a concrete local-first reference pattern
- **Protocol acknowledgment tokens** belong to the visible **Runtime Contract section**
- `STATE_USE`, `STATE_MOD`, and `STATE_DEL` may return `STATE_ERR_NOT_FOUND`
- **Inspection commands** return an **Inspection response shape**
- The **Canonical JSON payload** is the standard payload format for inspection responses
- Runtime errors return an **Error response shape**
- Successful mutators return a **Mutation response shape**
- **Task Profiles** should stay outside the MDP core and live in advanced details
- MDP enforces a **Single primary control token** per turn
- MDP requires **Explicit domain scoping** as a core invariant
- The **Hybrid domain model** uses one **Active domain** for retrieval defaults while keeping writes explicitly scoped
- **STATE_INIT** creates domains explicitly
- **STATE_USE** selects the **Active domain**
- `STATE_ADD` requires an **Explicit node identifier**
- Node IDs are **Global node identifiers** across all domains
- A **Global node identifier** counts as an **Explicit scoped reference**
- `STATE_DEL` deletes nodes, while **STATE_DROP** deletes entire domains
- MDP exposes **Inspection commands** in the runtime contract
- **STATE_LIST** enumerates domain contents, while **STATE_GET** inspects one node
- `STATE_LIST --domains` enumerates available domains
- `STATE_LIST` always requires an explicit selector
- Memory hygiene is one capability within **Memory Domain Control**, not the whole context

## Example dialogue

> **Dev:** "Is this gist mainly a memory purge preset?"
> **Domain expert:** "No - the product is a **Protocol-first** operating model. Memory purge is only one capability inside the **Memory Domain Protocol (MDP)**."
>
> **Dev:** "Does the prompt itself guarantee privacy and determinism?"
> **Domain expert:** "No - this is a **Two-layer standard**. The prompt shapes behavior immediately, but runtime code enforces the hard guarantees."
>
> **Dev:** "Should the standard assume an elite architect persona?"
> **Domain expert:** "No - keep a **Role-neutral core** and offer an **Architect Profile** as an optional overlay."
>
> **Dev:** "What do users call `#transform` and `#summarize`?"
> **Domain expert:** "Publicly, they are **Control tokens**. Canonically use `#transform`, `#refactor`, `#intent`, and `#summarize`; internally, they route the session into an **Execution state**."
>
> **Dev:** "What exactly does `#transform` do?"
> **Domain expert:** "It is the **Composite control token**: emit a transformed primary artifact, a concise intent model, and a TASK vs ENVIRONMENT constraint split."
>
> **Dev:** "Does every non-standard control token need to show TASK and ENVIRONMENT explicitly?"
> **Domain expert:** "Yes - MDP uses a **Visible constraint split** for every non-standard primary control token."
>
> **Dev:** "What problem is MDP mainly solving?"
> **Domain expert:** "The primary failure mode is **State contamination**. When users need a more concrete label, call the symptom **Contextual bleed**."
>
> **Dev:** "Are all original modules part of the standard?"
> **Domain expert:** "No - **Constraint Modularization** is core. **Semantic Delta** and **Token Metrics** are optional overlays."
>
> **Dev:** "What does the `GDPR Ready` badge mean here?"
> **Domain expert:** "It signals engineering alignment with privacy-first operation and explicit state control, not legal certification."
>
> **Dev:** "How does MDP talk to both humans and runtimes?"
> **Domain expert:** "Use a **Dual interface**: **Control tokens** for operators and **State mutators** for machine-parseable state changes."
>
> **Dev:** "What should the runtime contract look like?"
> **Domain expert:** "Make a **CLI-like DSL** canonical for humans and operators, then show JSON only as an optional transport mapping."
>
> **Dev:** "How should the gist title balance authority and virality?"
> **Domain expert:** "Use a **Two-line title stack**: the formal standard name first, then a broader mission-control subtitle."
>
> **Dev:** "Should the standard require Unix or POSIX analogies?"
> **Domain expert:** "No - remove that entirely. The public standard should use **Platform-neutral language**."
>
> **Dev:** "Should `#constraint:[...]` replace the whole baseline?"
> **Domain expert:** "No - it should be a **Scoped override** that only replaces conflicting rules for the current turn."
>
> **Dev:** "What should `#summarize` produce?"
> **Domain expert:** "A **Portable session bootstrap artifact**: reusable state for later sessions, but not a replacement system prompt."
>
> **Dev:** "Should the runtime interface be hidden in advanced docs?"
> **Domain expert:** "No - put a visible **Runtime Contract section** in the main body and hide only the JSON transport mapping inside `<details>`."
>
> **Dev:** "What does `Local-First: Validated` mean?"
> **Domain expert:** "It means MDP was engineered against a concrete local-first reference pattern with operator-owned state and no assumed cloud memory, not that it was externally certified."
>
> **Dev:** "How should a runtime acknowledge `STATE_*` mutations?"
> **Domain expert:** "Use **Protocol acknowledgment tokens** like `STATE_OK`, `STATE_ERR_INVALID`, and `STATE_ERR_POLICY`."
>
> **Dev:** "How should the runtime report a missing domain or node?"
> **Domain expert:** "Use `STATE_ERR_NOT_FOUND` so missing targets are distinguishable from malformed commands."
>
> **Dev:** "How should inspection commands return data?"
> **Domain expert:** "Use an **Inspection response shape**: a status token first, then a structured payload below it."
>
> **Dev:** "What structured payload format should inspection responses use?"
> **Domain expert:** "Use a **Canonical JSON payload** after the status token. Keep the command surface CLI-like, but make the inspection payload machine-parseable JSON."
>
> **Dev:** "Should runtime errors carry machine-readable detail too?"
> **Domain expert:** "Yes - use an **Error response shape**: error token first, then a compact JSON payload describing the failure."
>
> **Dev:** "Should successful mutation commands return more than `STATE_OK`?"
> **Domain expert:** "Yes - use a **Mutation response shape**: `STATE_OK` first, then a compact JSON payload confirming the operation."
>
> **Dev:** "Where do code review and architecture critique behaviors belong?"
> **Domain expert:** "In optional **Task Profiles**, not in the MDP core."
>
> **Dev:** "Can I stack multiple primary control tokens in one message?"
> **Domain expert:** "No - MDP enforces a **Single primary control token**. If multiple appear, the operator must choose one."
>
> **Dev:** "Is domain scope optional in MDP?"
> **Domain expert:** "No - **Explicit domain scoping** is a core invariant. Cross-domain access must never be implicit."
>
> **Dev:** "What is a domain in MDP?"
> **Domain expert:** "A **Domain** is a bounded work context: a project, workstream, problem space, or long-lived objective-level state boundary."
>
> **Dev:** "Do I need to repeat the domain on every retrieval?"
> **Domain expert:** "No - use the **Hybrid domain model**. Retrieval defaults to the **Active domain**, but writes still declare their domain explicitly."
>
> **Dev:** "How do I switch the active domain?"
> **Domain expert:** "Use `STATE_USE --domain <name>`. That is the canonical runtime command for selecting the **Active domain**."
>
> **Dev:** "How are nodes identified for later mutation?"
> **Domain expert:** "Require an **Explicit node identifier** with `STATE_ADD --id <name>` so follow-up operations target stable nodes."
>
> **Dev:** "Are node IDs unique only within a domain?"
> **Domain expert:** "No - MDP uses **Global node identifiers** so a node can be targeted directly across all domains."
>
> **Dev:** "Does direct node targeting violate explicit domain scoping?"
> **Domain expert:** "No - a **Global node identifier** is itself an **Explicit scoped reference**. Node-level responses should include the owning domain."
>
> **Dev:** "Can `STATE_DEL` remove a whole domain?"
> **Domain expert:** "No - `STATE_DEL` deletes nodes only. Use **STATE_DROP** with `STATE_DROP --domain <name>` for whole-domain deletion."
>
> **Dev:** "How does a domain get created in the first place?"
> **Domain expert:** "Use **STATE_INIT** with `STATE_INIT --domain <name>`. Domain creation is explicit, never implicit."
>
> **Dev:** "Is retrieval only implicit behind the active domain?"
> **Domain expert:** "No - MDP also exposes **Inspection commands** so operators can inspect state explicitly."
>
> **Dev:** "What read verbs should the protocol expose?"
> **Domain expert:** "Split them: use **STATE_LIST** to enumerate a domain and **STATE_GET** to inspect one node."
>
> **Dev:** "How do I enumerate available domains?"
> **Domain expert:** "Use `STATE_LIST --domains`."
>
> **Dev:** "Can `STATE_LIST` default to the active domain with no selector?"
> **Domain expert:** "No - `STATE_LIST` always requires an explicit selector such as `--domains` or `--domain <name>`."

## Flagged ambiguities

- "memory purge" was used to describe the whole asset - resolved: it is a subsystem capability, not the primary product identity.
- "Memory Domain Control" and "Memory Domain Protocol" were competing as the public title - resolved: **Memory Domain Protocol (MDP)** is the public standard name, while **Memory Domain Control** names the underlying discipline.
- "deterministic" and "privacy-ready" risked sounding like prompt-only guarantees - resolved: the gist will use a **Two-layer standard** framing, separating behavioral guidance from runtime enforcement.
- the original "Senior Systems Architect" persona risked making the standard look personal and exclusionary - resolved: the gist will keep a **Role-neutral core** with an optional **Architect Profile**.
- `KDBT` was too insider-heavy for the public interface - resolved: the gist will use **Control tokens** publicly and reserve **Execution state** for architectural description.
- several competing "villains" were present in the drafts - resolved: the gist will center **State contamination** as the core failure mode and use **Contextual bleed** as the memorable symptom.
- the original modules were too heavy to all remain mandatory - resolved: **Constraint Modularization** stays in the core, while **Semantic Delta** and **Token Metrics** become optional overlays.
- Constraint Modularization still risked being invisible in some prompt modes - resolved: every non-standard primary control token will emit a **Visible constraint split** with `TASK` and `ENVIRONMENT`.
- `GDPR Ready` could be misread as certification - resolved: the badge stays, but the gist will define it as an engineering-alignment signal with an explicit non-legal disclaimer.
- the protocol surface was split between chat-friendly hooks and runtime commands - resolved: the gist will adopt a **Dual interface** with **Control tokens** for operators and **State mutators** for runtimes.
- the runtime surface needed a canonical syntax - resolved: **CLI-like DSL** is the primary syntax for **State mutators**, while JSON appears only as an optional mapping.
- the public heading needed both authority and hook value - resolved: the gist will use a **Two-line title stack** with `The Memory Domain Protocol (MDP)` over `Universal Mission Control for Local-First Agents`.
- `#mirror` was too opaque for new readers - resolved: the public standard will rename it to `#transform`.
- `#transform` was still underspecified after the rename - resolved: it will be the **Composite control token** for transformed artifact + intent model + constraint modularization.
- the Unix/POSIX/open-source metaphor lock made the standard too narrow - resolved: the public standard will drop platform-specific metaphor rules and use **Platform-neutral language**.
- `#constraint:[...]` was too destructive in the original draft - resolved: it becomes a **Scoped override** of conflicting rules only, never a full baseline replacement.
- `#summarize` was previously framed as a next-session system prompt - resolved: it will output a **Portable session bootstrap artifact** instead.
- the runtime-facing contract risked being buried - resolved: the gist will include a visible **Runtime Contract section** and keep JSON mapping inside `<details>`.
- `Local-First: Validated` risked reading like an undefined badge - resolved: it will be defined as engineering validation against a concrete local-first reference pattern.
- the runtime acknowledgment format was too prose-like - resolved: the standard will use **Protocol acknowledgment tokens** such as `STATE_OK`, `STATE_ERR_INVALID`, and `STATE_ERR_POLICY`.
- missing domains and nodes needed a distinct failure mode - resolved: the runtime will return `STATE_ERR_NOT_FOUND` for absent targets.
- inspection commands previously lacked a response contract - resolved: they will use an **Inspection response shape** with a status token followed by a structured payload.
- inspection payload encoding was still underspecified - resolved: MDP will use a **Canonical JSON payload** for inspection responses.
- runtime errors were still too opaque for tooling - resolved: MDP will use an **Error response shape** with an error token followed by a compact JSON payload.
- successful mutations were still too terse for deterministic tooling - resolved: MDP will use a **Mutation response shape** with `STATE_OK` followed by a compact JSON payload.
- the original procedural behaviors were too opinionated for the core protocol - resolved: they move into optional **Task Profiles** inside advanced details.
- stacked primary tokens would have made routing ambiguous - resolved: MDP will allow a **Single primary control token** per turn and ask the operator to choose if multiple appear.
- the role of domains was still underspecified - resolved: MDP will require **Explicit domain scoping** for state operations and scoped retrieval.
- `Domain` itself was still too fuzzy - resolved: a **Domain** is a bounded work context, not a user identity or global memory pool.
- fully explicit domain repetition would have added too much operator friction - resolved: MDP will use a **Hybrid domain model** with one **Active domain** for retrieval defaults and explicit domain scope on writes.
- the hybrid model needed a canonical domain-selection command - resolved: `STATE_USE --domain <name>` will select the **Active domain**.
- node mutation needed stable referential integrity - resolved: `STATE_ADD` will require an **Explicit node identifier** via `--id`.
- node identity scope was still ambiguous - resolved: MDP uses **Global node identifiers** across all domains.
- explicit domain scoping and direct node targeting were in tension - resolved: a **Global node identifier** counts as an **Explicit scoped reference**, and node responses include the owning domain.
- domain deletion was too dangerous to overload onto `STATE_DEL` - resolved: `STATE_DEL` deletes nodes only, while **STATE_DROP** deletes entire domains.
- domain lifecycle still had an implicit creation hole - resolved: domains are created explicitly via **STATE_INIT** with `STATE_INIT --domain <name>`.
- the runtime contract was write-heavy but inspection-light - resolved: MDP will expose explicit **Inspection commands** instead of relying only on implicit retrieval.
- the inspection path needed distinct verbs - resolved: MDP will split reads into **STATE_LIST** for domain enumeration and **STATE_GET** for single-node inspection.
- domain discovery still lacked a canonical surface - resolved: operators enumerate available domains with `STATE_LIST --domains`.
- inspection listing was still too implicit - resolved: `STATE_LIST` always requires an explicit selector rather than defaulting to the active domain.
