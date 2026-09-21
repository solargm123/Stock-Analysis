# Auth Safety Workflow

## State model
Unknown -> Logged Out -> Authenticating -> Logged In -> Logging Out -> Logged Out

## Required checks when auth code changes
1. Login with valid credentials.
2. Refresh/reload and restore session.
3. Logout.
4. Refresh after logout: user remains logged out.
5. Back-navigation/mobile flow does not restore a cleared local session.

## Rules
- UI state must not claim logged out while a usable session remains.
- Local cleanup should be reliable even when remote sign-out fails, while errors remain observable.
- Never log secrets/tokens.
- Do not alter unrelated portfolio data during auth transitions.
