# Tech Stack

FastAPI + SQLite + a single HTML page. Python backend, real persistence, no extra services.

## Choices

**Backend:** FastAPI. One module of REST routes is enough: list, create, move, delete.

**Database:** SQLite via SQLAlchemy. One file on disk, no Docker, no database server. Schema matches `_docs/specs.md`: `id`, `title`, `status`, `created_at`.

**Frontend:** Static HTML/CSS/JS served by FastAPI. Fetch the API, render three columns, buttons for create / move / delete. No React, no bundler.

## Why this stack

- Flask is equally simple; FastAPI is a bit nicer for JSON APIs and auto-docs at `/docs`.
- Postgres or Mongo add setup this homework does not need.
- GraphQL and a SPA are extra moving parts for three endpoints.

## Layout

```
app.py              # FastAPI app and routes
models.py           # Task table
static/index.html   # board UI
kanban.db           # created on first run
pyproject.toml      # dependencies (managed with uv)
uv.lock
```

Install with `uv sync`. Run with `uv run uvicorn app:app --reload`.

## API

- `GET /api/tasks`
- `POST /api/tasks` `{ "title": "..." }` → status `TODO`
- `PATCH /api/tasks/{id}` `{ "status": "IN_PROGRESS" }`
- `DELETE /api/tasks/{id}`

No auth, no drag-and-drop, no extra task fields — same as the spec.
