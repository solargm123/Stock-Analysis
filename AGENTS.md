# Stock-Analysis Agent Router

## Core mode
Use a credit-efficient workflow: reuse verified context, inspect only affected code, batch compatible changes, run targeted tests first, and avoid unrelated refactors.

## Route by task
- Portfolio, BUY/SELL, Holdings, Average Cost, Realized/Unrealized P/L, Dime CSV -> read `.skills/portfolio-accounting.md`
- Market Price, quote refresh, Edge Function, cache, API failure -> read `.skills/market-data.md`
- Login, logout, session, mobile auth -> read `.skills/auth-safety.md`
- Bug, button not working, unknown failure -> read `.skills/bug-triage.md`
- Ambiguous, complex, underspecified, suspicious, or multi-path request -> read `.skills/clarification-gate.md`
- Repeated workflow/pattern worth standardizing -> read `.skills/skill-evolution.md`
- Performance measurement/logging -> read `.skills/performance-log.md`
- Any code change that may affect existing behavior -> read `.skills/regression-guard.md`

## Clarify before execute
If the request is complex, ambiguous, missing key details, suspicious, or has multiple materially different implementation paths, do not start editing immediately. First:
1. Identify what is unclear or suspicious.
2. Explain the risk or ambiguity briefly.
3. Ask only the minimum questions needed, or propose one concrete interpretation with assumptions.
4. Confirm scope, expected behavior, protected behavior, and completion criteria.
5. Start implementation only after the task is sufficiently unambiguous.

Do not ask questions when the request is already clear enough to execute safely.

## Suspicious command flagging
Always call out commands that may:
- delete/reset/overwrite production data,
- alter accounting or historical transaction results,
- weaken auth/RLS/permissions,
- expose secrets or tokens,
- push destructive changes directly to main,
- change market-data behavior in a way that can corrupt portfolio value,
- refer to an unclear "old version", "latest file", or "same as before" when multiple candidates exist.

## Protected behavior
Do not change transaction history semantics, average-cost accounting, holdings calculations, P/L logic, auth/session behavior, or market-data contracts unless explicitly required.

## Default execution
Clarify if needed -> identify affected flow -> load only relevant skill -> edit smallest surface -> targeted test -> regression guard -> review diff -> one coherent commit -> lightweight performance log.

See `WORKFLOW-NOTE.md` for the visual map.
