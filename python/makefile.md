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

# ── Platform detection ───────────────────
ifeq ($(OS),Windows_NT)
  PYTHON   := python
  RUNPY    := $(VENV)/Scripts/python.exe
  ACTIVATE := $(VENV)/Scripts/activate.bat
  RUFF     := $(VENV)/Scripts/ruff.exe
else
  RUNPY    := $(VENV)/bin/python
  ACTIVATE := $(VENV)/bin/activate
  RUFF     := $(VENV)/bin/ruff
endif

# Always invoke pip as “python -m pip”
PIP := $(RUNPY) -m pip

.PHONY: setup run lint format test clean help

setup: $(ACTIVATE)

$(ACTIVATE):
	$(PYTHON) -m venv $(VENV)
	$(RUNPY) -m pip install --upgrade pip
	$(RUNPY) -m pip install -r requirements.txt

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
