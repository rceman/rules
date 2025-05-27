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

# Detect OS: Scripts/ on Windows, bin/ on Unix
ifeq ($(OS),Windows_NT)
  PIP   := $(VENV)/Scripts/pip.exe
  RUNPY := $(VENV)/Scripts/python.exe
  RUFF  := $(VENV)/Scripts/ruff.exe
else
  PIP   := $(VENV)/bin/pip
  RUNPY := $(VENV)/bin/python
  RUFF  := $(VENV)/bin/ruff
endif

.PHONY: setup run lint format test clean help

setup: $(VENV)/bin/activate

$(VENV)/bin/activate: pyproject.toml
	$(PYTHON) -m venv $(VENV)
	$(PIP) install --upgrade pip
	$(PIP) install -r requirements.txt
	$(PIP) freeze > requirements.txt
	touch $@

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
