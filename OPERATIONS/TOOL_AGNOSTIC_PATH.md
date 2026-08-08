# TOOL_AGNOSTIC_PATH

## Purpose

This file defines the tool-agnostic operating path of the workspace.

It exists to clarify that the Engineering Work Doctrine and the governance layer of this workspace are not structurally dependent on any specific AI tool.

---

## Doctrine Agnosticism

The Engineering Work Doctrine is implemented as structured markdown files.

It requires no specific AI tool to operate correctly.

Any AI that:
- reads `AGENTS.md` at the workspace root
- applies the behavioral activation rules embedded there
- follows the lifecycle defined in `ENGINEERING_WORK_DOCTRINE/03_PROJECT_LIFECYCLE.md`
- respects operational states (Exploratory, Formative, Stable) defined in `ENGINEERING_WORK_DOCTRINE/21_OPERATIONAL_STATES.md`
- uses the discovery and consolidation protocols
- applies the readiness gate before delivery
- applies mega-tech protocols (files 23-34) proportionally to state and work type

...is operating correctly under the doctrine, regardless of tool identity.

---

## Tool Compatibility

| AI Tool | Primary Activation | Status |
|---------|-------------------|--------|
| Codex (OpenAI) | `AGENTS.md` | Current preferred path |
| Claude (Anthropic) | `AGENTS.md` | Compatible |
| Gemini (Google) | `AGENTS.md` | Fallback path |
| Windsurf / Cascade | `AGENTS.md` | Compatible |
| Cursor | `AGENTS.md` | Compatible |
| Any LLM with file access | `AGENTS.md` | Compatible |

---

## What Any Tool Needs

For any AI to operate correctly under this doctrine:

1. Read `AGENTS.md` at workspace root — this activates doctrinal behavior (v0.8.1: includes operational states, mega-tech awareness, five-layer architecture, ecosystem structure, root model)
2. Apply the lifecycle, decision rules, and quality standards embedded there
3. Respect operational states: classify work as Exploratory, Formative, or Stable before applying rules
4. For deeper rules: read `ENGINEERING_WORK_DOCTRINE/` files as needed (35 files, 00-34)
5. For compact activation: use `ENGINEERING_WORK_DOCTRINE/14_RUNTIME_MASTER_PROMPT.md`
6. For mega-tech protocols: read files 23-34 as relevant to the work type and state
7. Respect the absolute rule: no project creation outside doctrinal action

---

## What No Tool Should Do

Regardless of which tool is active:

- Do not bypass lifecycle stages
- Do not create project files before readiness is established
- Do not require the user to provide technical vocabulary
- Do not treat inferred elements as confirmed
- Do not ignore the discovery phase
- Do not confuse enthusiasm or conversational length with readiness

---

## Tool Preference vs Structural Dependency

These are different things.

**Tool preference** — Codex is the current preferred execution path. This is a strategic decision recorded in `DECISIONS/0002_MAIN_AI_PATH.md`. It reflects the current phase and available resources.

**Structural dependency** — None. The doctrine, governance layer, and project lifecycle work correctly with any AI that can read markdown and apply behavioral instructions.

Changing the preferred tool does not change the doctrine.

---

## Activation Guarantee

The `AGENTS.md` at workspace root is designed to be the single activation artifact that any AI tool can consume to operate doctrinally.

It contains:
- immediate behavioral rules
- lifecycle order
- core decision rules
- environment description
- links to full doctrine

This guarantees that no manual prompt injection by the user is required for doctrine-governed behavior to begin.

---

## Success Condition

This tool-agnostic path is working correctly when:

- any AI with `AGENTS.md` access activates doctrine-compliant behavior without manual prompting
- project quality and lifecycle discipline are equivalent across different AI tools
- no structural breakage occurs when the preferred tool changes
- the doctrine governs behavior regardless of which tool executes it
