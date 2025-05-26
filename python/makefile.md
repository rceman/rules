# 🛠️ Makefile Rules

Use **Make** to unify common tasks.

| Target | Purpose                           |
|--------|-----------------------------------|
| setup  | create venv & install deps        |
| run    | run app / CLI                    |
| lint   | run linter                        |
| format | apply formatter                   |
| test   | run pytest                        |
| clean  | remove artefacts                  |

```makefile
PYTHON ?= python3
VENV   ?= .venv
PIP    := $(VENV)/bin/pip
RUNPY  := $(VENV)/bin/python
RUFF   := $(VENV)/bin/ruff

.PHONY: setup run lint format test clean help

$(VENV)/bin/activate: pyproject.toml
	$(PYTHON) -m venv $(VENV)
	$(PIP) install --upgrade pip
	$(PIP) install -r requirements.txt
	touch $@

setup: $(VENV)/bin/activate

run: setup
	$(RUNPY) -m package_name

lint:
	$(RUFF) check src tests

format:
	$(RUFF) format .

test:
	$(RUNPY) -m pytest -q

clean:
	rm -rf $(VENV) **/__pycache__ dist build *.egg-info
```
