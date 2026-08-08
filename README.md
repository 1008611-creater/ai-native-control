# AI Native Control

This private repository is the shared fact layer for Codex and Hermes. It stores project registration and reviewable handoff records. It does not store application source code, user media, credentials, session transcripts, or deployment secrets.

## Roles

- Codex is the only engineering writer. It changes source code, tests, releases, and fixes.
- Hermes is the continuous operations worker. It observes registered targets, runs scheduled checks, and creates evidence-backed handoffs.
- The user owns priority, external commitments, credentials, paid actions, deletion, and other irreversible decisions.

## Layout

- `registry/projects.yaml` registers a project, its public targets, and its assigned owners.
- `schemas/handoff.schema.json` defines the minimum handoff envelope shared by both agents.
- `handoffs/` contains reviewable task records. One task is one JSON file.

## Handoff cycle

1. Codex publishes or repairs a project and records the release reference and expected state.
2. Hermes observes that target and records a handoff only when an action is needed.
3. Codex accepts the engineering handoff, makes the change, and records verification evidence.
4. Hermes performs the follow-up observation and closes the record or creates the next actionable handoff.

The JSON envelope is intentionally shaped for a future A2A adapter, but it is not yet a live A2A service. Until the adapter exists, Git commits are the durable transport and the user starts Codex work locally.

