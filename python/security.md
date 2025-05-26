# 🔒 Security Rules

* **Secrets** – never commit. Use environment variables and provide `.env.example`.
* **Bandit** – run static security analysis: `bandit -r src`.
* **Dependency scanning** – use `pip-audit` in CI.
* **Permissions** – Docker images run as non‑root.
