# Stock-Analysis Agent Router

## Core mode
Use a credit-efficient workflow: reuse verified context, inspect only affected code, batch compatible changes, run targeted tests first, and avoid unrelated refactors.

## Route by task
- Portfolio, BUY/SELL, Holdings, Average Cost, Realized/Unrealized P/L, Dime CSV -> read `.skills/portfolio-accounting.md`
- Market Price, quote refresh, Edge Function, cache, API failure -> read `.skills/market-data.md`
- Login, logout, session, mobile auth -> read `.skills/auth-safety.md`
- Bug, button not working, unknown failure -> read `.skills/bug-triage.md`
- Ambiguous, complex, underspecified, multi-path request -> read `.skills/clarification-gate.md`
- Repeated workflow/pattern worth standardizing -> read `.skills/skill-evolution.md`
- Any code change that may affect existing behavior -> read `.skills/regression-guard.md`

## Clarify before execute
If the request is complex, ambiguous, missing key details, or has multiple materially different implementation paths, do not start editing immediately. First make the work concrete by:
1. Identifying what is unclear.
2. Asking only the minimum questions needed, or proposing a specific recommended interpretation when a question is unnecessary.
3. Confirming scope, expected behavior, protected behavior, and completion criteria.
4. Starting implementation only after the task is sufficiently unambiguous.

Do not ask questions when the request is already clear enough to execute safely.

## Protected behavior
Do not change transaction history semantics, average-cost accounting, holdings calculations, P/L logic, auth/session behavior, or market-data contracts unless explicitly required.

## Default execution
Clarify if needed -> identify affected flow -> load only relevant skill -> edit smallest surface -> targeted test -> regression guard -> review diff -> one coherent commit.

See `WORKFLOW-NOTE.md` for the visual map.
