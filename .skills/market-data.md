# Market Data Resilience

## Data path
UI -> Cached Quote -> Edge Function -> Market Provider

## Display rules
- Live quote available -> show quote + updated timestamp.
- Provider/API failure -> keep last valid cached quote + show stale/last-updated state.
- No valid quote -> show N/A, never fabricate 0.

## Safety
- Quote refresh must not create or mutate transactions.
- Quote refresh must not change average cost.
- Avoid API calls on every component render.
- Debounce repeated refresh actions.
- Keep symbol normalization at one boundary.
- Surface non-2xx errors in user-friendly form while retaining diagnostic detail for logs.

## Testing
Check: successful refresh, cached fallback, no-cache failure, repeated click, session-expired/API failure.
