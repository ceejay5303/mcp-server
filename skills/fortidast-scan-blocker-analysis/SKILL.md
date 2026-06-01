---
name: fortidast-scan-blocker-analysis
description: Use when diagnosing FortiDAST scans that are stopped, incomplete, failed, unauthenticated, unable to crawl authenticated areas, or otherwise blocked.
---

# FortiDAST Scan Blocker Analysis

Use this skill when the user asks why a scan is stopped, stuck, incomplete, unauthenticated, or low-confidence.

## Workflow

1. If the asset URL or UUID is unclear, call `list_assets`.
2. Call `auth_status` to inspect FortiDAST target authentication/configuration state.
3. Call `scan_status` to inspect scan status, progress, scan errors, response metrics, and request count.
4. Explain the observed state from FortiDAST before making any inference.
5. Recommend FortiDAST-side checks such as target reachability, authentication setup, scan configuration, service availability, and scan logs.

## Output

Return observed auth state, observed scan state, likely blocker class, evidence supporting that assessment, and next checks.

## Boundaries

This connector cannot fix blockers directly because it is read-only. Do not claim to start, stop, authenticate, or reconfigure the target.
