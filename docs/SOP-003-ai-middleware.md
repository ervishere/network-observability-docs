# SOP-003: Gemini AI Middleware & UI Deployment

## 1. Overview
A custom FastAPI Python application that queries Loki logs via LogQL, streams context to the Gemini API (`gemini-3.6-flash`), and serves a Tailwind CSS web UI.

## 2. Deployment
*   **Location:** `/opt/gemini-noc/`
*   **Dependencies:** `fastapi`, `uvicorn`, `google-generativeai`, `requests`.
*   **Execution:** Managed by Supervisor. Listens on `http://127.0.0.1:8000`.

## 3. UI Features
The integrated frontend (`/static/index.html`) provides natural language querying, time range selection (15m, 1h, 6h, 24h), severity filtering, and raw log evidence extraction.
