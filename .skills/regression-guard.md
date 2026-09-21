# Regression Guard

Use for every non-trivial change.

## Before edit
1. Name the requested behavior.
2. List protected behaviors that must remain unchanged.
3. Identify the smallest affected files/functions.
4. Avoid touching unrelated code.

## Protected Stock flows
- Login/session restore/logout
- Transaction history integrity
- BUY/SELL quantity math
- Average cost
- Holdings aggregation
- Realized and unrealized P/L
- Market price refresh and cache fallback
- Mobile and desktop primary actions

## After edit
Run the cheapest reliable checks:
1. Syntax/static check.
2. Targeted feature check.
3. One adjacent protected-flow check when shared code changed.
4. Final diff review for accidental changes, secrets, debug code, and duplicated logic.

Do not run a full regression suite unless the change is cross-cutting.
