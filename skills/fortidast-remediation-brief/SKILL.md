---
name: fortidast-remediation-brief
description: Use when converting FortiDAST scan findings into developer-facing remediation guidance, grouped fix themes, ticket-style actions, and acceptance criteria.
---

# FortiDAST Remediation Brief

Use this skill when the user asks for a remediation plan, engineering handoff, Jira-style tickets, or developer-facing fix guidance.

## Workflow

1. If the asset URL or UUID is unclear, call `list_assets`.
2. Call `scan_status` to confirm whether detailed findings are valid to use.
3. Call `get_scan_summary` to identify vulnerability themes.
4. Call `get_scan_results` to collect affected URLs, evidence, impact, and remediation text.
5. Group findings by root cause or vulnerability type instead of creating one task per duplicate URL.

## Output

Return prioritized remediation tasks with title, priority, affected URLs, evidence summary, recommended fix, acceptance criteria, and scan caveats.

## Boundaries

Use FortiDAST-provided remediation and evidence when available. Do not fabricate code changes, proof of exploitation, or ownership details. This connector is read-only and cannot create tickets or change FortiDAST state.
