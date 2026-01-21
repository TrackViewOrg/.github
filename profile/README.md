# Trackview

> **Record. Analyze. Improve.**
> The automated telemetry dashboard for serious sim racers.

---

## 🔒 Internal Organization Hub
This repository serves as the central source of truth for **Trackview** assets, track data, and static configurations. It allows the separation of application logic (source code) from the heavy static data required for the racing ecosystem.

## 🏗 Architecture Overview

The Trackview ecosystem consists of three distinct high-performance layers:

1.  **Client (Tauri):** Local ingestion engine. Hooks into Assetto Corsa shared memory.
2.  **Processing (Python/FastAPI):** The intelligence layer. Cleans raw telemetry and generates insights.
3.  **Dashboard (Next.js):** The presentation layer. Renders high-frequency data using Recharts.

```mermaid
graph LR
    A[Assetto Corsa] -->|Shared Memory| B[Tauri Client]
    B -->|Raw JSON| C[Supabase Storage]
    C -->|Trigger| D[Python API]
    D -->|Analysis & Insights| E[Supabase DB]
    E -->|Clean Data| F[Next.js Dashboard]
