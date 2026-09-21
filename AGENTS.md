# Stock-Analysis Agent Router

## Core mode
Use a credit-efficient workflow: reuse verified context, inspect only affected code, batch compatible changes, run targeted tests first, and avoid unrelated refactors.

## Route by task
- Portfolio, BUY/SELL, Holdings, Average Cost, Realized/Unrealized P/L, Dime CSV -> read `.skills/portfolio-accounting.md`
- Market Price, quote refresh, Edge Function, cache, API failure -> read `.skills/market-data.md`
- Login, logout, session, mobile auth -> read `.skills/auth-safety.md`
- Bug, button not working, unknown failure -> read `.skills/bug-triage.md`
- Any code change that may affect existing behavior -> read `.skills/regression-guard.md`

## Protected behavior
Do not change transaction history semantics, average-cost accounting, holdings calculations, P/L logic, auth/session behavior, or market-data contracts unless explicitly required.

## Default execution
Identify affected flow -> load only relevant skill -> edit smallest surface -> targeted test -> regression guard -> review diff -> one coherent commit.

See `WORKFLOW-NOTE.md` for the visual map.
