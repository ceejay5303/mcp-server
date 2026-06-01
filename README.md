# FortiDAST MCP

FortiDAST MCP lets Claude securely read FortiDAST scan data and use guided security-analysis skills for faster DAST review.

## What You Can Ask

- List my FortiDAST assets.
- Which scans are complete, stopped, or not started?
- Review the posture of this application.
- Show the most important vulnerabilities for this scan.
- Why did this scan stop or fail?
- Create a remediation brief for engineering.
- Compare risk across completed scans.

## Included Skills

- Asset inventory
- Scan posture review
- Vulnerability triage
- Scan blocker analysis
- Executive risk summary
- Remediation brief
- Scan comparison

## Connector Capabilities

This connector is read-only. It can retrieve:

- FortiDAST assets
- Scan status
- Target authentication status
- Scan summary results
- Detailed scan findings

It does not start scans, stop scans, create assets, delete assets, or change FortiDAST configuration.

## Connect In Claude

1. Open Claude.
2. Go to **Customize**.
3. Add this repository as a personal plugin.
4. Open the FortiDAST MCP connector.
5. Click **Connect**.
6. Enter your FortiDAST username and API key when prompted.

Claude can then use the FortiDAST connector and skills in chat.

## Authentication

Your FortiDAST username and API key are entered on the FortiDAST MCP onboarding page. The connector validates them with FortiDAST before enabling access.

Use an API key that belongs to your FortiDAST account and has access to the assets you want Claude to review.

## Current Scope

This is a read-only FortiDAST MCP connector for Claude plugin testing and review workflows.
