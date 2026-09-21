# Stock-Analysis Workflow Note

## Which skill should run?

```mermaid
flowchart TD
    A[New request] --> B{Task type}
    B -->|BUY SELL Holdings P/L CSV| C[Portfolio Accounting]
    B -->|Price Refresh Quote API| D[Market Data]
    B -->|Login Logout Session| E[Auth Safety]
    B -->|Unknown bug / button broken| F[Bug Triage]
    C --> G[Regression Guard]
    D --> G
    E --> G
    F --> G
    G --> H[Targeted test]
    H --> I[Diff review]
    I --> J[One coherent commit]
```

## Portfolio data flow

```mermaid
flowchart LR
    T[Transactions] --> P[Position Engine]
    P --> H[Holdings]
    H --> M[Portfolio Metrics]
    Q[Market Quote] --> M
    Q -. must not change .-> C[Cost Basis]
    T --> C
```

## Short operating note
For UI-only work, stay in UI unless evidence points elsewhere. For accounting changes, protect transaction invariants first. For market refresh problems, preserve the last valid quote instead of turning portfolio value into zero. For auth changes, always verify refresh + logout + mobile/back-navigation behavior.
