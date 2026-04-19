# matter-drill-down

**Plugin:** LPM Core
**Repo:** Private (LPMHub)
**Licence:** Apache-2.0

## What this skill does

Produces an LPM working view on a single matter. Structured around deliverables, issues, and risks. The output is for the LPM's own operational use, not for distribution to partners or clients. Four modes cover the common single-matter invocation patterns: standard drill-down, decision-first view, partner call prep, and handoff briefing.

## Modes

| Mode | Name | When to use |
|---|---|---|
| 1 | Standard drill-down | Default. "Drill into [matter]", "focus on [matter]", "brief me on [matter]". |
| 2 | Decision-first | "What do I need to decide on [matter]?", "open decisions on [matter]". |
| 3 | Partner prep | "Prep me for [partner] call on [matter]", "before the call with [partner]". |
| 4 | Handoff briefing | "I'm handing [matter] to [name]", "leave cover on [matter]", "taking over [matter]". |

## Key outputs by mode

**Mode 1:** .docx with identifier header, summary, deliverables table, issues, risks, open decisions, scope signals, financial position (one paragraph), team/stakeholder state, cross-matter context, and handoffs. 2-3 pages.

**Mode 2:** Decision-focused .docx. Open decisions expanded (decision statement, owner, options, blockers, LPM recommendation). Issues and risks retained. Supporting sections collapsed to one line each. See usage notes below.

**Mode 3:** .docx reshaped for an upcoming partner call. Adds: decisions required from the partner, information the partner may not have, likely partner questions with prepared answer lines. Standard tables retained. 2-4 pages.

**Mode 4:** Extended .docx for matter handoff. Adds: outstanding commitments, tacit knowledge section (prompted from outgoing LPM, not fabricated), who-to-call table by issue type, stakeholder tone snapshot, scheduled touchpoints. 4-6 pages.

## Usage notes

**Mode 2 — use explicit document language.** When triggered by a natural-language question ("What do I need to decide on Meridian?"), the skill may produce conversational advisory prose rather than a structured .docx. This is a known v1 limitation. To ensure document output, prompt with: "Produce a decision-first drill-down on [matter] as a .docx." The decision content is consistently high quality in both formats; only the output structure is affected.

**Mode 4 — tacit knowledge section.** The "What Is Not Visible in the Matter Files" section is not populated from the correspondence. The skill prompts the outgoing LPM with specific questions about relationship dynamics, communication preferences, partner behaviour, and client-side politics. If the outgoing LPM does not provide answers, the section remains as prompts. This is by design. The handoff briefing is incomplete without this content.

**Audience check.** If you ask for a report intended for a partner or client audience, the skill may produce a client-facing status report rather than routing to `status-report-drafter`. This is a known v1 limitation. For client-facing reports, invoke `status-report-drafter` directly.

**Identifier gate.** The skill may infer matter identifiers from correspondence rather than asking when identifiers are not explicitly provided. Low operational risk but identifiers should be confirmed for formal .docx records.

**Restraint.** Quiet matters produce short output. The skill does not pad empty sections or normalise length across matters.

## What it doesn't do

This skill does not produce status reports for distribution (use `status-report-drafter`), portfolio-level briefings across multiple matters (use `daily-briefing`), RAID log updates (use `risk-and-issues-manager`), scope change memos (use `scope-change-controller`), or budget variance analysis (use `budget-and-fee-manager`).

## Skills this one works with

| Skill | Handoff |
|---|---|
| daily-briefing | Invoked from daily-briefing Mode 2 (single-matter routing) or LPMHub click-through |
| scope-change-controller | Scope signals requiring formal assessment |
| risk-and-issues-manager | RAID log updates from drill-down findings |
| status-report-drafter | Partner/client-facing reporting (different register) |
| local-counsel-manager | LC non-response or escalation patterns |
| budget-and-fee-manager | Detailed financial analysis beyond the one-paragraph position |
| stakeholder-comms-planner | Client communication plans or decks |
| timeline-generator | Programme timeline impact analysis or what-if scenarios |
| resource-planner | Team or cover arrangements |

## Design principles applied

- DP-26: Global input classification before mode selection
- DP-27: Template skeletons as populated templates, not descriptions
- Produce-don't-ask: no conditional offers
- Summary label (not BLUF)
- Identifier gate (hard gate before production)
- Handoff language aligned with adjacent skills
- No named firms in templates or domain knowledge
- Source tag preservation for attributed inputs

## Phase 2 status

Complete. Tested on Opus 4.6. Modes 1, 3, 4 passed. Mode 2 and audience routing documented as v1 limitations with workarounds.

## Licence

Apache-2.0. See LICENSE in repo root.
