# VS Code Agents Instructions

This file provides instructions for AI coding agents working with the VS Code codebase.

For detailed project overview, architecture, coding guidelines, and validation steps, see the [Copilot Instructions](.github/copilot-instructions.md).

## Cloud Agent environment

Development commands need the Node.js version in `.nvmrc`. The Cloud Agent image also puts an older `node` earlier on `PATH`. Login shells load `/etc/profile.d/cursor-node.sh`, which prefers `/usr/local/bin`. If `node -v` does not match `.nvmrc`, run `export PATH="/usr/local/bin:$PATH"` before `npm` or `node`.

From the repository root:

- `node build/npm/fast-install.ts` installs dependencies when lockfiles changed.
- `npm run build-fast` compiles the desktop client and built-in extensions.
- `npm run compile-web` compiles built-in extensions for VS Code for the Web.
- `./scripts/test.sh --run <test-file>` runs one Electron unit test. Set `DISPLAY` when a display server is available.
- `./scripts/code-web.sh --host 0.0.0.0 --port 8080 --browserType none` serves the web workbench.
