# 🐳 Docker Rules

## Image Guidelines

* Base on `python:3.11-slim`.
* Copy only `poetry.lock` / `requirements.txt` first to leverage layer caching.
* Use a **non‑root** user inside the container.

### Example Dockerfile

```dockerfile
FROM python:3.11-slim
WORKDIR /app

# leverage layer caching
COPY pyproject.toml poetry.lock ./
RUN pip install poetry && poetry install --no-dev

COPY src/ src/
CMD ["python", "-m", "package_name"]
```
