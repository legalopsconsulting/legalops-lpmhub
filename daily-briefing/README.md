# daily-briefing

**Plugin:** LPM Core
**Repo:** Private (LPMHub)
**Licence:** Apache-2.0

## What this skill does

Produces a portfolio-level morning briefing for an LPM running two or more active matters. Reads email, call notes, and matter state across the portfolio and produces a triage surface structured around deliverables, issues, and risks. The output is a working document for the LPM's own consumption, not for distribution.

## Modes

| Mode | Name | When to use |
|---|---|---|
| 1 | Portfolio briefing | Default. "Run my daily briefing" across 2+ matters. |
| 2 | Single-matter routing | User pastes single-matter input. Routes to `matter-drill-down`. Does not produce a briefing. |
| 3 | Monday sweep | "Run my Monday sweep." Adds Weekend Developments and Week-Ahead Calendar Overlay sections. |
| 4 | Ad-hoc timeframe | "What's landed in the last 48 hours?" Bounds content to a specified window. |

## Key outputs by mode

**Mode 1 / Mode 3:** .docx with identifier block, portfolio summary, deliverables ranked across matters, issues, risks, cross-matter patterns, scope signals, partner attention items, matter mini-briefings (sized to weight, not normalised), reading list (max 5), calendar overlay (Mode 3 only), and handoffs.

**Mode 2:** No output. Routes to `matter-drill-down`.

**Mode 4:** Same template as Mode 1, bounded to the specified timeframe.

## Usage notes

**Cross-matter ranking.** Deliverables are ranked across the portfolio, not grouped by matter. This is the discipline that separates a portfolio briefing from a stack of status reports.

**Restraint on quiet matters.** Green matters with nothing live get 1-2 lines in the mini-briefing. The skill does not pad quiet matters to normalise length. Empty sections are stated plainly.

**Attribution.** Substantive analysis from named individuals is attributed by name. Generic attribution to "the team" is the failure mode.

**Single-matter input.** If you paste correspondence for only one matter, the skill will not produce a portfolio briefing. It routes to `matter-drill-down`. This is by design. Use `matter-drill-down` for single-matter views.

## What it doesn't do

This skill does not produce single-matter drill-downs (use `matter-drill-down`), audience-facing status reports (use `status-report-drafter`), RAID log updates (use `risk-and-issues-manager`), or any other single-matter operational output. It is the portfolio layer only.

## Skills this one works with

| Skill | Handoff |
|---|---|
| matter-drill-down | Single-matter zoom-in from portfolio view (Mode 2 routing) |
| scope-change-controller | Scope signals detected across the portfolio |
| risk-and-issues-manager | Risk or issue patterns surfaced at portfolio level |
| status-report-drafter | Partner/client reporting needs identified |
| local-counsel-manager | LC non-response or escalation patterns |
| budget-and-fee-manager | Fee pressure or variance patterns across matters |
| resource-planner | LPM or partner load pressure across matters |
| stakeholder-comms-planner | Client communication needs identified |

## Design principles applied

- DP-26: Global input classification before mode selection
- DP-27: Template skeletons as populated templates, not descriptions
- Produce-don't-ask: no conditional offers
- Summary label (not BLUF)
- Identifier gate on every output header
- Handoff language aligned with adjacent skills
- No named firms in templates or domain knowledge

## Phase 2 status

Complete. Tested on Opus 4.6 and Sonnet. Cross-model validation confirmed.

## Licence

Apache-2.0. See LICENSE in repo root.
