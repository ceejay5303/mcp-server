---
name: fortidast-executive-risk-summary
description: Use when creating a business-facing FortiDAST risk summary across assets, including scan coverage, highest-risk applications, severity distribution, and recommended leadership next steps.
---

# FortiDAST Executive Risk Summary

Use this skill when the user asks for a leadership, management, or portfolio-level summary of FortiDAST posture.

## Workflow

1. Call `list_assets`.
2. Summarize scan coverage by status and progress.
3. Rank assets by `threat_level`, prioritizing completed scans.
4. For high-risk completed assets, call `get_scan_summary` to avoid over-fetching detailed results.
5. Do not call `get_scan_results` unless the user explicitly asks for technical detail.

## Output

Return overall posture, scan coverage gaps, highest-risk assets, severity/category themes, business impact framing, and recommended next steps.
Note: You may ask the user if they would like an interactive HTML/CSS canvas or in-chat visualisation

## Boundaries

Keep the response concise and business-oriented. Do not overstate risk for incomplete scans; call out scan-quality caveats. This connector is read-only and cannot change scan configuration.
