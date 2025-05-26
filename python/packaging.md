# 📦 Packaging Rules

If you publish to PyPI:

1. Use **PEP 621** metadata in `pyproject.toml`.
2. Provide `__version__` via `importlib.metadata`.
3. Build wheels via `python -m build`.
4. Tag releases with *semantic versioning* (`v1.2.0`).
