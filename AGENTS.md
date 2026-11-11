# Project guidance

nx2android ports the user's Switch games to Android: rewritten ARM64 game code runs natively, with Horizon services implemented by the host and NVN graphics replayed through Vulkan.

## Layout

- `porter/`: CLI and port/build/install pipeline; `gui/`: PySide6 UI over that pipeline.
- `nxnative/dm/host/` and `gfx/`: shared runtime and graphics core.
- `nxnative/dm/android/`: Android runtime, Vulkan backend and APK tooling.
- `nxnative/dm/games/<title ID>/`: game profiles and per-build patches.
- `tests/`: automated checks; `devtools/`: device diagnostics.

## Environment and commands

Use the project interpreter `.venv\Scripts\python.exe` (Python 3.14); avoid the global Conda environment. Dependencies are in `requirements.txt`.

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m porter doctor
.\.venv\Scripts\python.exe -m gui
.\.venv\Scripts\python.exe -m unittest discover tests
```

## Working rules

- Read `docs/ARCHITECTURE.md` and `docs/DEVELOPMENT_GUIDE.md` for implementation and build details; respect nested `AGENTS.md` files.
- Keep game-specific facts in profiles; implement general fixes in the shared core and preserve iOS compatibility. Follow surrounding style and write code, comments and documentation in English.
- Local game inputs and existing build data are in `ns_games/` (ignored). Keep new test builds and diagnostics under `.gamedump/<App>/`; never commit game files, keys, saves or generated packages.
- Measure before optimizing. Compare the same scene and settings; distinguish CPU replay, GPU timestamp spans, hardware utilization and presentation delays.
- Obtain user authorization before device installation; prefer a separate test package and preserve the user's installation and saves. Restore temporary test settings.
- Run relevant checks after code changes and the full test suite before committing. Commit, push or publish only when requested; preserve unrelated user edits.
- Device workflows: `.claude/skills/nx2android-dev/SKILL.md` and `.claude/skills/switch-android-port/SKILL.md`; additional repository conventions: `CLAUDE.md`.

## Git identity

- This user's fork belongs to `lianghx123`. Use the user's effective Git identity (`git config user.name` and `git config user.email`); the current identity is `lianghx123 <huangxin711@163.com>`.
- The user explicitly overrides the legacy instruction in `nxnative/AGENTS.md` that hard-codes `seedds`. Do not use that command or override author/committer identity unless the user requests it. Three repair commits were initially attributed to `seedds` by that inherited command; their identity was corrected at the user's request.
- Preserve the authors of upstream commits. Rewrite published history only with explicit user authorization and protect remote updates with `--force-with-lease`.
