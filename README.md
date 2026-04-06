# ai-dev-base

Lightweight base image for AI agent development with [Gas City](https://github.com/gastownhall/gascity) orchestration.

## What's included

| Category | Tools |
|----------|-------|
| **Orchestration** | `gc` (Gas City), `bd` (Beads), `dolt` |
| **AI CLIs** | `claude`, `codex`, `amp` |
| **System** | `git`, `tmux`, `jq`, `curl`, `gh`, `zsh`, `bash` |

## What's NOT included

This is a **base image**. It does not include language runtimes (Node, Python, Go), package managers, or project-specific tooling. Build a downstream image for your use case:

```dockerfile
FROM ghcr.io/dataviking-tech/ai-dev-base:edge

# Add your stack
RUN sudo apt-get update && sudo apt-get install -y nodejs npm python3
```

## Usage

### Docker

```bash
docker pull ghcr.io/dataviking-tech/ai-dev-base:edge
docker run -it ghcr.io/dataviking-tech/ai-dev-base:edge
```

### Devcontainer

See [ai-dev-base-devcontainer](https://github.com/DataViking-Tech/ai-dev-base-devcontainer) for a ready-made devcontainer template.

```json
{
  "image": "ghcr.io/dataviking-tech/ai-dev-base:edge"
}
```

## Tags

| Tag | Description |
|-----|-------------|
| `edge` | Latest from `main` branch (nightly) |
| `v1` | Latest v1.x.x release |
| `v1.0` | Latest v1.0.x release |
| `v1.0.0` | Immutable release |

## Pinned versions

| Tool | Version |
|------|---------|
| Gas City (gc) | 0.13.4 |
| Beads (bd) | 1.0.0 |
| Dolt | 1.85.0 |

## Building locally

```bash
# Single arch
docker build -t ai-dev-base .

# Multi-arch
docker buildx build --platform linux/amd64,linux/arm64 -t ai-dev-base .
```

## License

MIT
