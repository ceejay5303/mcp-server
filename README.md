# FortiDAST MCP Server

Python implementation of a read-only FortiDAST MCP server using the official `mcp` SDK and the FortiDAST Swagger-backed endpoints already present in `FortiDAST_RestApi_Swagger.yaml`.

## Current capability surface

### Tools

- `list_assets`
- `auth_status`
- `scan_status`
- `get_scan_summary`
- `get_scan_results`

### Resources

- `fortidast://connection/status`
- `fortidast://assets/catalog`

### Prompts

- `summarize_asset_posture`
- `investigate_scan_blockers`

State-changing FortiDAST operations such as asset creation/deletion, authentication configuration, scan start, and scan stop are intentionally out of scope for this connector version.

### Tool Usage Guidance

- Use `list_assets` first to discover canonical asset URLs and UUIDs.
- Use `scan_status` before fetching results to check whether a scan is complete, stopped, not started, or still in progress.
- Use `get_scan_summary` before `get_scan_results` for posture assessment.
- Use `get_scan_results` only when individual findings, evidence, impact, or remediation details are required because detailed result payloads can be large or slow.
- Use `auth_status` only to inspect existing authentication/scan-auth state; this connector does not configure target credentials.


## Package selection

Direct runtime dependencies are pinned in [pyproject.toml](/home/mvrahul/fortidast_mcp/pyproject.toml):

- `mcp==1.27.0`
- `cryptography==47.0.0`
- `httpx==0.28.1`
- `idna==3.15`
- `pydantic==2.13.3`
- `starlette==1.0.1`
- `uvicorn==0.46.0`

The resolved environment should be re-audited after dependency changes with:

```bash
. .venv/bin/activate
pip-audit -r requirements.lock.txt
```

## Environment

Copy `.env.example` to `.env` and fill in the relevant section:

- `MCP_PUBLIC_BASE_URL`, such as your public ngrok URL during local testing
- `FORTIDAST_CREDENTIAL_STORE_KEY`

Generate a local credential-store key with:

```bash
. .venv/bin/activate
python - <<'PY'
from cryptography.fernet import Fernet
print(Fernet.generate_key().decode())
PY
```

`MCP_PUBLIC_BASE_URL` and `FORTIDAST_CREDENTIAL_STORE_KEY` are required.

## Claude Web Local Testing

Claude Web cannot reach `localhost` directly. Expose the local server through HTTPS:

```bash
. .venv/bin/activate
export MCP_PUBLIC_BASE_URL=https://your-tunnel.example
export FORTIDAST_CREDENTIAL_STORE_KEY=...
python -m fortidast_mcp
```

In another terminal:

```bash
ngrok http 8080
```

Then add this custom connector URL in Claude Web:

```text
https://your-tunnel.example/mcp
```

Claude should discover the protected resource metadata, register an OAuth client, redirect to `/oauth/connect`, and ask for the user's FortiDAST username and API key.

## Install

```bash
python3 -m venv .venv
. .venv/bin/activate
pip install -e .
```

## Run

```bash
. .venv/bin/activate
python -m fortidast_mcp
```

The MCP server is exposed over Streamable HTTP at `http://127.0.0.1:8080/mcp`.

## Operational endpoints

- `GET /healthz`
- `GET /me`
- `GET /v1/user/fortidast-credentials`
