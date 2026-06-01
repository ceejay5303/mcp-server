---
name: fortidast-scan-posture-review
description: Use when reviewing the FortiDAST security posture of a specific asset, including scan state, threat level, vulnerability summary, and whether detailed findings are needed.
---

# FortiDAST Scan Posture Review

Use this skill when the user asks to review, assess, summarize, or explain the security posture of one FortiDAST asset.

## Workflow

1. If the asset URL or UUID is unclear, call `list_assets` first.
2. Call `scan_status` before retrieving vulnerability data.
3. If the scan is complete, call `get_scan_summary`.
4. Only call `get_scan_results` when the user asks for detailed findings, evidence, payloads, impact, remediation, or top vulnerabilities.
5. If the scan is stopped, incomplete, not started, or failed, explain the observed scan state and avoid treating missing findings as a clean result.

## Output

Return scan state, scan progress, threat level, severity/category summary, top risk themes, scan-quality caveats, and the recommended next step.

## Boundaries

This connector is read-only. Do not claim to rerun, reconfigure, start, or stop scans.
