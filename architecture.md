# Architecture Overview

## Logical flow

1. **Source systems** provide asset, maintenance, and production context.
2. A **SQL curated layer** standardises asset hierarchy, status values, and operational KPIs.
3. A **semantic model** exposes governed business definitions for consumers.
4. Dashboards, analysts, and an **AI maintenance copilot** consume the same trusted layer.

## Source systems

- **Asset Registry** – asset hierarchy, class, installation, criticality
- **SAP PM / Work Orders** – work order type, status, planning, backlog, risk
- **Production Context** – deferred production, uptime, production impact
- **Condition / Sensor Signals** – supporting signal layer for prioritisation

## Why this matters for AI

AI consumers are highly sensitive to inconsistent definitions and low-trust data.
This design reduces failure risk by making ownership, lineage, quality and usage constraints explicit.
