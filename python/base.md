# 🏗️ Base Python Project Rules

The minimal rules every Python repo **MUST** follow, regardless of size or domain.

## 1&nbsp;&nbsp;Directory Layout

```
project/
├── pyproject.toml   ← PEP 621 metadata & deps
├── README.md
├── LICENSE
├── .gitignore
├── src/             ← all importable code lives here
│   └── package_name/
└── tests/           ← mirrors src layout
```

*No top‑level `.py` files.*  
Keep the root tidy—only configuration & docs.

## 2&nbsp;&nbsp;Python Version

* Target **Python 3.11+** unless you have a strong SLA to support lower.
* Declare it in `pyproject.toml`:

```toml
[project]
requires-python = ">=3.11"
```

## 3&nbsp;&nbsp;Commit Hygiene

*Use Conventional Commits* (`feat:`, `fix:`, `chore:`, `docs:` …).  
Never push directly to **main**; open a PR and require review.

---
