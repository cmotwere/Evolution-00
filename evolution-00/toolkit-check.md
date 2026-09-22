# Toolkit Check — Evolution 0

Installed and verified on: 2026-09-21

## uv + Python 3.14
```
$ uv --version
uv 0.12.17 (635500036 2026-09-18 x86_64-pc-windows-msvc)

$ uv run --python 3.14 python --version
Python 3.14.7
```
Note: uv manages Python versions itself rather than reading a single system
`python` on PATH — the system default `python` remains 3.12.10, and 3.14.7
is invoked through `uv run --python 3.14` (or a `.python-version` file /
`uv venv --python 3.14` inside a project directory).

## gzkit
```
$ gz --version
gzkit 0.34.7
```

## Ollama
```
$ ollama list
NAME           ID              SIZE      MODIFIED
llama3.2:1b    baf6a787fdff    1.3 GB    just pulled
```

## Harness — Claude Code
```
$ claude --version
2.1.268 (Claude Code)
```

## VS Code and git
```
$ code --version
1.138.0
7debcd0e2acdea1c52de81bf9ee1620444407dda
x64

$ git --version
git version 2.55.0.windows.4
```

## Notes / issues encountered
- `uv`, `gzkit`, and an Ollama model were not yet installed as of the toolkit
  check; all three were installed today (`uv` via the official Windows
  installer script, `gzkit` via `uv tool install py-gzkit`,
  `llama3.2:1b` via `ollama pull llama3.2:1b`).
- System-default `python` is 3.12.10 (Windows PATH). Python 3.14.7 is
  installed and managed through `uv` rather than replacing the system
  default — this is uv's normal model (per-project/per-invocation Python
  pinning) rather than a leftover issue.
