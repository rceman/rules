# 🧪 Testing Rules

* Framework: **pytest**.
* Directory: `tests/` at project root, mirrors `src/`.
* Keep unit tests fast—\<100 ms each. Integration tests may be slower.

## Coverage

* Use `pytest --cov` and aim for **80 %+**.
* Treat coverage drop \> 2 % as build failure.

## Fixtures

Store shared fixtures in `tests/conftest.py`.  
Prefer factory fixtures over global state.

## Parametrisation

Use `pytest.mark.parametrize` liberally—don’t copy‑paste near‑duplicates.

## Markers

| Marker                  | Meaning                               |
|-------------------------|---------------------------------------|
| `@pytest.mark.unit`     | pure logic, no I/O                    |
| `@pytest.mark.integration` | touches FS / network / DB        |
