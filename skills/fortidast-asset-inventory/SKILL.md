---
name: fortidast-asset-inventory
description: Use when the user asks to list FortiDAST assets, summarize scan coverage, identify completed or incomplete scans, or rank assets by threat level.
---

# FortiDAST Asset Inventory

Use this skill for inventory, scan coverage, and asset-level prioritization questions.

## Workflow

1. Call `list_assets`.
2. Use returned `scan_status`, `scan_progress`, `threat_level`, `asset_validated`, and `uuid` fields to summarize coverage.
3. Group assets by scan state: complete, running, stopped, not started, failed, or unknown.
4. Rank completed assets by `threat_level` when the user asks for risk prioritization.
5. Do not call detailed scan result tools unless the user asks for asset-specific findings.

## Output

Return a concise table with asset URL, UUID, scan status, progress, validation status, and threat level. Then provide a short coverage summary and recommended next step.

## Boundaries

This connector is read-only. Do not claim to create assets, delete assets, start scans, stop scans, or change scan configuration.
