# Memory Domain Control

> **Tagline:** A protocol for domain-scoped agent state and policy-gated memory

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Privacy: Local--First](https://img.shields.io/badge/Privacy-Local--First-brightgreen.svg)](#)
[![Architecture: Agentic](https://img.shields.io/badge/Architecture-Agentic-orange.svg)](#)

> **Status:** Draft standard | **Version:** 3.1.0  
> **Domain:** Agent state management and local-first orchestration  
> **Project/Org Label:** Aimergent

Most agent failures are not model failures. They are state failures.

When one memory pool is reused across unrelated tasks, terms, assumptions, and priorities leak. This is **Contextual Bleed**. It looks like intelligence drift, but in many cases it is state contamination.

Memory Domain Control is a practical protocol for making state explicit, scoped, and auditable. It does not replace engineering controls; it makes them easier to define and operate, especially when persistent memory features are enabled.

---
<p align="center">
<img src="https://raw.githubusercontent.com/Aimergentix/memory-domain-control/main/docs/images/banner.png" alt="A banner: The central structure is a large, glowing, semi-translucent amber core, emitting a soft, pulsing, bioluminescent light. This core is intricate, with stabilized internal fractal patterns, and is subtitled in a precise, glowing font: CORE. Radiating from this central hub, multiple smooth, curved, semi-translucent biological tendrils, resembling fiber-silk, form perfectly self-contained, closed-loop pathways. Each loop is hermetically sealed within a larger protective, semi-transparent sphere, visually representing cryptographic-style sandboxing. The golden, warm-toned light within these pathways pulsates rhythmically, simulating data flow without any connection to the external deep indigo and dark moss background. At the apex of each closed loop sits a distinct, rounded, sealed pod, thick-walled and containing stable, organized cell clusters, labeled in glowing characters as ISOLATED STATE POD and LOCAL STATE DATABASE. The atmosphere is dark, velvety, and entirely lit by the internal bioluminescence of the structure, casting diffused, soft light. All edges are rounded, organic, and self-contained. Annotation tags, rendered in soft glowing script, highlight different functions, such as Deterministic Loop B, Domain Isolation A, and Zero-Leak State C. A stylized, stabilized, regional-agnostic particle field drifts far in the background, out of focus and completely disconnected. The entire banner is framed by a soft, glowing, biopolymer border." width="900" />
</p>

## 1) Problem and scope

The term *harness* is too weak for modern agent runtimes. A harness implies passive restraint. Production systems need active control: state boundaries, authority boundaries, and interruption paths.

This document targets teams building local-first or privacy-sensitive agent workflows. It defines a command contract (`STATE_*`), a runtime routing model, and an implementation pattern for editor-integrated agents.

---

## 2) Protocol contract

### Guarantees (when implemented in runtime code)

- State writes are explicit and machine-parseable.
- State is segmented by domain.
- Every mutation is auditable.
- Execution can enforce domain-scoped retrieval.
- Persistent memory can be read-gated and write-gated by policy.

### Non-guarantees

- Prompt text alone cannot enforce security policy.
- This protocol does not prevent prompt injection by itself.
- Determinism is bounded: model sampling behavior still exists unless separately constrained.
- Persistent memory without scoping will still cause contextual bleed.

Use this protocol as a control surface between user intent and runtime policy, not as a substitute for RBAC, sandboxing, or middleware validation.

---

## 3) Memory terminology (for product teams)

When teams discuss "memory pool," they often mix separate mechanisms. Use precise terms:

- **Context window:** Tokens available to the model for one request.
- **Session memory:** Current thread history reused within one conversation.
- **Persistent memory:** Cross-session user facts or preferences saved for later reuse.
- **Memory interference (contextual bleed):** Old preferences/themes leaking into an unrelated task.
- **Memory scoping:** Restricting memory read/write access by domain, project, or task type.

Examples of persistent-memory style product features exist across major vendors (names and rollout vary by product and region): OpenAI (ChatGPT Memory), Google (Gemini saved info and history-based personalization), Anthropic (Claude project-level instructions and memory-like context reuse patterns), Microsoft (Copilot personalization/memory features), Meta (Meta AI memory features in supported surfaces).

---

## 4) Memory Domain Control syntax (state mutators)

Use explicit commands when you want parseable state transactions instead of conversational memory updates.

### Command forms

- `STATE_ADD --domain <name> --content "<data>"`
- `STATE_MOD --target <node_id> --update "<new_data>"`
- `STATE_DEL --target <domain_or_node>`

### Example commands

- `STATE_ADD --domain architecture --content "Use POSIX-style process analogies."`
- `STATE_MOD --target db_choice --update "Migrated to PostgreSQL."`
- `STATE_DEL --target legacy_codebase`

### Runtime behavior

- On successful mutation, reply with: `[State Synchronized]`
- On parse failure, reply with: `[State Error: Invalid Command]`
- On policy failure, reply with: `[State Error: Policy Violation]`

---

## 5) System directive template

Drop this template into your system prompt or orchestration layer. Keep policy enforcement in code.

```text
# SYSTEM DIRECTIVE: MEMORY DOMAIN CONTROL INITIALIZATION

You operate under the Memory Domain Control protocol.

Rules:
1) Treat each domain as isolated state unless explicitly linked.
2) Do not import assumptions from prior tasks without retrieval from active domain state.
3) Process STATE_ADD, STATE_MOD, and STATE_DEL as explicit mutation requests.
4) Confirm successful mutation with "[State Synchronized]".
5) If a command is invalid or blocked by policy, return a state error message.

Note: Security and permission checks are enforced by runtime policy, not by this prompt.
```

---

## 6) Architectural blueprint (runtime flow)

```text
                        Memory Domain Control Runtime

  +----------------------+        +------------------------------+
  |      System Admin    | -----> |   MDC Router                 |
  |  Dispatch: STATE_*   |        |   Domain lock + task route   |
  +----------------------+        +---------------+--------------+
                                                  |
                                                  v
                               +----------------------------------+
                               |        Local State Store         |
                               |   domain index + node history    |
                               +----------------+-----------------+
                                                |
                    +---------------------------+---------------------------+
                    |                           |                           |
                    v                           v                           v
        +------------------------+   +------------------------+   +------------------------+
        |       Audit Path       |   |     Mutation Path      |   |    Execution Path      |
        | append-only logs       |   | validate + apply write |   | fetch scoped context   |
        | + diff snapshots       |   | return status message  |   | run tool/model step    |
        +-----------+------------+   +-----------+------------+   +-----------+------------+
                    |                            |                            |
                    +----------------------------+----------------------------+
                                                 |
                                                 v
                         +------------------------------------------+
                         |          Operator-Facing Output          |
                         | audit trail | state status | task result |
                         +------------------------------------------+
```

Where enforcement lives:
- Command parsing: router layer
- Permission checks: policy middleware
- State persistence: local store
- Tool invocation control: execution gateway

---

## 7) Memory Domain Control vs. harness

| Architecture dimension | Traditional "harness" framing | Memory Domain Control framing |
| --- | --- | --- |
| State management | Implicit context reuse | Explicit `STATE_*` mutation contract |
| Domain integrity | Soft conversational boundaries | Domain-scoped state and retrieval |
| Execution authority | Prompt-weighted suggestions | Runtime-checked policy gates |
| Auditability | Partial chat history | Structured mutation and event logs |
| Local-first posture | Often cloud-anchored | Compatible with local-only pipelines |

---

## 8) IDE integration (`.cursorrules`)

For editor agents, enforce the interaction contract at workspace level:

```markdown
# Memory Domain Control

- Treat this repository as an isolated domain.
- If a message starts with `STATE_ADD`, `STATE_MOD`, or `STATE_DEL`, parse it as a state command.
- On success, reply only: `[State Synchronized]`
- On invalid command: `[State Error: Invalid Command]`
- On policy violation: `[State Error: Policy Violation]`
- Do not execute privileged actions without explicit runtime approval.
```

---

## 9) Adoption checklist

Use these checks before calling your system "agentic" in production:

1. **State scope:** Can you list active domains and their assumptions?
2. **Mutation path:** Are state changes explicit, parseable, and logged?
3. **Authority boundary:** Is there a hard boundary between model proposals and executable actions?
4. **Interruption path:** Can an operator halt an in-flight run immediately?

If any answer is "no," the system still depends on implicit memory and conversational drift.

Memory Domain Control is not a branding layer. It is an operational discipline: explicit state, bounded authority, auditable change.
