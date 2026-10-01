---
name: grafana-backend-run
description: "Run Grafana locally with disk-backed Go build temporary directories when RAM-backed /tmp can cause memory exhaustion; verify the host storage layout before using workstation-specific examples."
---

# Grafana backend run guide

Use a disk-backed directory for large Go build temporary files when the host's default `/tmp` is RAM-backed.

## Check the host

From the Grafana repository root, inspect the filesystem for both `/tmp` and the proposed cache location:

```bash
df -hT /tmp "$HOME"
```

The original guide describes Nikshay's workstation, where `/tmp` is tmpfs and the home directory is SSD-backed. Verify those properties on the current host. If the home directory is also RAM-backed, choose another writable disk-backed location with sufficient free space.

## Run the backend

For a disk-backed home directory:

```bash
mkdir -p "$HOME/.cache/grafana-go-tmp"
export TMPDIR="$HOME/.cache/grafana-go-tmp"
export GOTMPDIR="$HOME/.cache/grafana-go-tmp"

printf '%s\n' "$TMPDIR" "$GOTMPDIR"
make run
```

`GOTMPDIR` controls Go's temporary build files. `TMPDIR` covers other tools involved in the build. The exports apply to the current shell session; repeat or verify them in a fresh terminal before running the backend. Follow the checked-out Grafana repository's own setup instructions if its commands differ.

If the frontend is needed, run `yarn start` in a separate terminal after completing the repository's frontend setup. Account for the combined memory use of the backend and frontend.

## Troubleshoot

Read [the original workstation guide](references/original-run-guide.md) for memory, disk-space, cache-size, and mount checks. Its absolute `/home/nikshay` paths describe that workstation; use the current user's paths instead.

The reference also contains optional cache-deletion commands. Use those only when cleanup is requested or authorized, after stopping active builds and confirming the exact rebuildable directories. Do not change shell configuration or remove caches merely to start Grafana.
