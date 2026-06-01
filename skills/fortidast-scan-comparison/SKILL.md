---
name: fortidast-scan-comparison
description: Use when comparing FortiDAST scan posture across multiple assets, ranking completed scans by risk, or identifying which application needs deeper review first.
---

# FortiDAST Scan Comparison

Use this skill when the user asks to compare assets, rank completed scans, or decide which scanned application needs attention first.

## Workflow

1. Call `list_assets`.
2. Filter or group assets by scan status and progress.
3. Rank completed scans by threat level.
4. For selected high-risk completed assets, call `get_scan_summary`.
5. Avoid calling `get_scan_results` across many assets unless the user confirms they need detailed findings.

## Output

Return a comparison table, risk ranking, scan coverage notes, category/severity differences, and recommended follow-up.

## Boundaries

Do not compare incomplete scans as if they are final. Always mention scan status and progress when comparing assets. This connector is read-only and cannot rerun scans.
