# 📦 Dependency & Virtual‑env Rules

1. **Lock File**

   Use *Poetry* or *Hatch* for dependency resolution and commit `poetry.lock` / `hatch.lock`.  
   For raw **pip**, commit a fully‑pinned `requirements.txt`.

2. **Virtual Environment**

   ```
   python -m venv .venv
   source .venv/bin/activate
   ```

   Exclude `.venv/` in `.gitignore`.

3. **Optional Extra Files**

   * `requirements-dev.txt` for lint / test tools.  
   * `requirements-ai.txt` if LLM/VLM packages balloon compile times.
