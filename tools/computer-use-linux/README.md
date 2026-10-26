# Linux Computer Use MCP

This crate vendors the Linux Computer Use MCP server used by the ChatGPT
Community Linux project. It exposes desktop screenshots, accessibility trees,
window inspection, keyboard and pointer input, and terminal context over MCP
stdio transport.

## Build

From the Codex++ repository root:

```bash
cargo build -p codex-computer-use-linux --release
install -Dm755 target/release/codex-computer-use-linux \
  "$HOME/.local/bin/codex-computer-use-linux"
```

The runtime is Linux-only. Wayland sessions normally need the XDG Remote
Desktop portal; GNOME sessions may also need accessibility enabled and the
optional GNOME Shell window-targeting extension.

## MCP configuration

The stdio server entry is:

```toml
[mcp_servers.computer-use-linux]
command = "codex-computer-use-linux"
args = ["mcp"]
```

The Linux Codex++ manager injects this entry automatically when it writes the
live Codex config. The same stdio configuration can also be used manually by a
ChatGPT desktop host that supports local MCP servers.

## Diagnostics

```bash
codex-computer-use-linux doctor
codex-computer-use-linux setup
codex-computer-use-linux apps
codex-computer-use-linux windows
codex-computer-use-linux screenshot
```

The original MIT license is kept in this directory. The source was copied
from the local `codex-desktop-linux` checkout and remains an independent
workspace member so upstream changes can be reviewed and synchronized
separately.
