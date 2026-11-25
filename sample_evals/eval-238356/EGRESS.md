# Agent egress notes (Harbor)

## agent-public
Inherited when the source run allows internet access. The environment and agent
have public internet access; the separate verifier remains `no-network`.

## public
Explicit override enabling public internet access for both agent and verifier.

## harbor-allowlist (default without a source run)
Follows Harbor's recommended phase split:
- `[environment] network_mode = "public"` so `agent.setup()` can install CLIs
- `[agent] network_mode = "allowlist"` restricts `agent.run()` to model API hosts
- `[verifier.environment] network_mode = "no-network"`

Requires Docker nftables FIB (`CONFIG_NFT_FIB_INET`) or another provider with
network policy support (OrbStack/Linux, Modal, E2B, …). **Docker Desktop
macOS typically rejects both `allowlist` and `no-network`** — use
`--egress public` for local Desktop smoke tests, OrbStack/Linux for real
isolation, or `--egress latch-proxy`.

## Claude Code
Disable server-side web tools (`WebSearch` / `WebFetch`) so they cannot bypass
the sandbox allowlist.

## Codex
With Harbor allowlist, dial `api.openai.com` directly (do **not** set HTTP_PROXY).

## latch-proxy
Emits `environment/docker-compose.yaml` with an internal network + CONNECT
allowlist proxy (+ Codex revproxy). Harbor baseline stays `public` because
compose + Harbor `allowlist` is unsupported on several providers. Isolation is
via the compose network, not Harbor nftables.
For Codex: `base_url=http://egress-revproxy:3129/v1` and avoid HTTP_PROXY.
Compose is mainly for local Docker; many cloud sandboxes are Dockerfile-only.
