Commands

- `uv sync` - install dependencies
- `uv run pytest` - the whole suite
- `uv run pytest tests/test_home.py` - one test file

Rules

- Use uv for all Python dependencies (`pyproject.toml` + `uv.lock`). Do not use
  `requirements.txt`.
- Dependencies are added in `pyproject.toml`. Do not add one without
  asking
