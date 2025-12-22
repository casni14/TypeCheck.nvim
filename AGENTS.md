# Repository Guidelines

## Project Structure & Module Organization
- `lua/typecheck/init.lua` contains the core session logic, rendering, and stats tracking.
- `plugin/typecheck.lua` defines Neovim user commands (`:TypeCheck`, `:TypeCheckStats`).
- `doc/typecheck.txt` is the `:h TypeCheck` help file; keep it in sync with user-facing changes.
- `README.md` documents installation and usage examples.

## Build, Test, and Development Commands
- There is no build step; this is a pure Lua Neovim plugin.
- Manual smoke test in Neovim:
  - `:TypeCheck` to start a session in the current buffer.
  - `:TypeCheckStats` to verify stats and history display.
- Help docs (if your setup doesn’t auto-generate tags): run `:helptags ALL` then `:h TypeCheck`.

## Coding Style & Naming Conventions
- Lua code lives under `lua/typecheck/`; keep modules lowercase and require via `require("typecheck")`.
- Match file-local indentation (tabs in `lua/typecheck/init.lua`, two spaces in `plugin/typecheck.lua`).
- Prefer `snake_case` for local functions and variables; user commands are `CamelCase` (`TypeCheck`).
- Avoid globals; use `local` and the module table `M`.

## Testing Guidelines
- No automated test framework is configured.
- For changes, describe manual test steps in your PR (buffer opened, command run, behavior observed).
- If you modify behavior or configuration, update both `README.md` and `doc/typecheck.txt`.

## Commit & Pull Request Guidelines
- Recent commits use short, descriptive messages (e.g., `feat: ...`, `docs: ...` or simple imperatives).
  Follow that style and keep the subject line concise.
- PRs should include:
  - A clear summary of the change.
  - Manual test steps or confirmation of behavior.
  - Documentation updates when user-facing behavior changes.

## Configuration & State Notes
- Session progress is persisted to `stdpath("state")/typecheck_progress.json`.
  Avoid breaking the on-disk format; add migration logic if needed.
