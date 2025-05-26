# 🔁 Continuous Integration Rules

If your project is CI‑enabled:

* Use GitHub Actions (or GitLab CI, Azure Pipelines, etc.).
* **Cache dependencies**: use `actions/cache` keyed by `poetry.lock` / `requirements*.txt`.
* Pipeline steps:

```yaml
- name: Setup
  run: make setup
- name: Lint
  run: make lint
- name: Test
  run: make test
```

*Fail‑fast*—no step after a failure.
