# Kanban Board MVP Specification

## 1. System Overview
A lightweight, single-board Kanban web application designed to demonstrate full-stack persistence (Frontend, REST/GraphQL API, Relational/NoSQL Database) with minimal UI overhead.

## 2. Target Features (MVP Scope)

### Feature 1: Board & Column Visualization
- **Description:** Render a fixed 3-column layout (*To Do*, *In Progress*, *Done*).
- **Behavior:** On page load, fetch all active tasks from the backend database and group them into their corresponding column.
- **Constraints:** Columns are static and hardcoded in code; no UI for adding or renaming columns.

### Feature 2: Basic Task Creation
- **Description:** Allow users to create new task items.
- **Fields:** `Title` (String, required).
- **Behavior:** Newly created tasks automatically default to the *To Do* status and persist immediately to the backend.

### Feature 3: Button-Based Status Movement & Deletion
- **Description:** Advance or regress tasks through workflow states using simple control buttons on each card.
- **Controls:**
  - `Move Left` / `Move Right` buttons (or a simple status dropdown).
  - `Delete` button to permanently remove a task.
- **Behavior:** Trigger an API call on click to update the task status in the database and refresh the UI state.

## 3. Non-Goals (Out of Scope for MVP)
- User authentication, user accounts, or authorization.
- HTML5 Drag-and-Drop drag events.
- Dynamic column management.
- Task details (descriptions, due dates, tags, assignees).

## 4. Suggested Data Schema

```sql
TABLE tasks (
    id VARCHAR(36) PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    status VARCHAR(20) NOT NULL CHECK (status IN ('TODO', 'IN_PROGRESS', 'DONE')),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
