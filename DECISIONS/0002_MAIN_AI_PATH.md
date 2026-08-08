# DECISION 0002 — MAIN AI PATH

> **Doctrine version:** 0.8.1

## Decision
Codex will be treated as the main AI operating path of the workspace.

## Why
The main path should consume the user's existing ChatGPT plan instead of depending on separate API billing.

## Practical Consequence
Gemini runtime remains fallback only.
Workspace preparation and project birth flow should now be stabilized around the Codex path.

## Constraint
The workspace must still be designed so that future CLI-first operation remains possible.

## Immediate Priority
Prepare the workspace so that the main path can operate cleanly and consistently over the doctrine and Projects structure.

## Agnosticism Note
This decision records a **tool preference** for the current phase, not a structural dependency.

The Engineering Work Doctrine and the governance layer are AI-agnostic. Any AI that reads `AGENTS.md` at the workspace root activates correctly under the doctrine, regardless of tool identity.

Changing the preferred tool in a future phase does not require changes to the doctrine.

See: `OPERATIONS/TOOL_AGNOSTIC_PATH.md`

## Doctrine Coverage
The main AI path must activate the full doctrine, including the 12 mega-tech protocols (files 23-34) for Stable state work. The AI path is responsible for determining Operational State, applying proportional process, and executing the Consolidation Moment ritual before work enters Stable state. See `ENGINEERING_WORK_DOCTRINE/14_RUNTIME_MASTER_PROMPT.md` for the compact activation.