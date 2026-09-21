# Portfolio Accounting Guard

## Source of truth
Transactions -> Position Engine -> Holdings -> Portfolio Metrics

Dashboard values must be derived from transaction/accounting state, not used as accounting input.

## BUY
- Increase quantity.
- Recalculate weighted average cost from existing open quantity and new purchase cost.
- Preserve transaction record.

## SELL
- Realized P/L = sold quantity x (sell price - average cost immediately before sale), adjusted only for explicitly modeled fees/taxes.
- Reduce open quantity.
- Do not retroactively rewrite historical BUY cost.
- Selling must not be driven by current market price unless explicitly selected by the user.

## Unrealized P/L
Use open quantity and current market price. Market price refresh must never alter cost basis.

## Import / Edit / Delete
- Normalize Dime CSV before insert.
- Detect likely duplicate transactions before creating duplicates.
- Recompute downstream holdings deterministically after transaction mutation.
- Validate no negative position unless short-selling is intentionally supported.

## Invariants
sum(open lots/position qty) = displayed holding qty
market refresh != transaction
cached quote != cost basis
realized P/L stays stable when only live price changes
