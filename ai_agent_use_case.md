# AI Agent Use Case – Maintenance Copilot

## Objective

Support planners and maintenance leads by identifying work orders that should be prioritised based on:
- asset criticality
- maintenance backlog
- production impact
- operational risk score

## Example prompt / workflow

> Which open work orders on critical offshore assets should be prioritised this week, and why?

## Required data-side guardrails

- The copilot must only use approved fields and approved data products.
- The response must include lineage/provenance references.
- High-risk recommendations must be treated as **decision support**, not autonomous action.
- Confidence should be reduced or warnings shown if source freshness or completeness checks fail.

## Why the data product matters

Without governed semantics, the agent may misinterpret:
- what counts as backlog
- how criticality is defined
- whether production impact is current or historical
- whether a work order is actually open, deferred, or closed
