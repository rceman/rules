# 🧹 Linting & Formatting Rules

| Tool  | Purpose                   | Config file      |
|-------|---------------------------|------------------|
| Ruff  | linter + formatter        | `pyproject.toml` |
| Black | optional auto‑formatter   | `pyproject.toml` |
| mypy  | static typing             | `mypy.ini`       |

**Rules**

* Lint *before* tests in CI; fail build on any error.
* Run `ruff format .` before committing (can be a pre‑commit hook).
* Target strictest reasonable `mypy` settings: `strict = True` but allow gradual typing via `# type: ignore`.
