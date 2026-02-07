# DATA_AND_REVIEW_MODEL.md

## Purpose

This document defines the **canonical data and review model** for the trading system.

It specifies:

- which data is collected,
- at which granularity,
- for which decision layer,
- and for which review ritual.

This file is the **single data contract** for all future tooling and automation.

---

## Design Principles

- Data exists to **support governance**, not optimization
- No data without a decision use-case
- Minimal, auditable, boring
- Same structure regardless of automation level
- Humans and LLMs must be able to reason from this alone

---

## Decision Layers

The system operates on three distinct decision layers:

1. **Execution Layer**  
   Intraday and strategy-local behavior

2. **Risk Kernel Layer**  
   Portfolio-level control and permissioning

3. **Context Layer**  
   External market understanding and regime awareness

Each data point belongs to **exactly one layer**.

---

## 1. Execution Layer Data (Per Trading System)

### STRATUM (Intraday Microstructure)

Purpose: verify stability, discipline, and drawdown control.

Required data:

- operating state (LIVE, SHADOW, FLAT)
- active session window
- equity start-of-day and current
- drawdown (day, week, month)
- open exposure (side, size, unrealized)
- trade count per day
- rolling win rate
- average R
- profit factor
- kill-switch activations (count and last reason)
- execution latency (if available)
- venue health indicators (disconnects, rejects)

No market predictions.
No indicators stored.

---

### ORBIT (Seasonal Regime Participation)

Purpose: verify eligibility, gate discipline, and churn avoidance.

Required data:

- season eligibility status
- gate pass or fail summary
- strategy state (IN_POSITION, CASH, COOLDOWN)
- current holding (ticker, size, entry)
- unrealized PnL
- monthly drawdown
- switch count per month
- order execution status

No intraday metrics.
No microstructure assumptions.

---

### ANCHOR (Long-Horizon Allocation)

Purpose: verify capital preservation and counterparty risk awareness.

Required data:

- allocation snapshot (BTC %, XAUT %, USD* %)
- monthly drawdown
- rebalance flag and rationale
- USD* composition (fiat vs stablecoin)
- effective USD after haircut

ANCHOR data changes slowly and is reviewed infrequently.

---

## 2. Portfolio-Level Data (Risk Kernel Inputs)

Purpose: enable global risk decisions.

Required data:

- portfolio NAV (start and current)
- portfolio drawdown (current and max)
- global operating state
- active system caps
- active overrides or pauses
- textual correlation or concentration notes (no models)

No scoring.
No forecasting.

---

## 3. Venue and Operational Health

Purpose: avoid trading blind during infrastructure stress.

Required data:

- connectivity status
- API error counts
- order reject counts
- balance availability confirmation

If venue health degrades, risk bias is towards reduction.

---

## 4. Communication Channels

### Telegram (Awareness Channel)

Telegram is used for **attention**, not storage.

Allowed messages:

- system state changes
- kill-switch activations
- drawdown threshold breaches
- connectivity events
- end-of-day summaries

No historical data.
No analytics.

---

### Google Account (Audit and Review Store)

Google storage is the **system memory**.

Stored items:

- daily snapshots
- weekly rollups
- monthly rollups
- completed review documents

All stored data must be explainable from this model.

---

## 5. Context Layer (Human + LLM)

Purpose: provide regime understanding beyond internal metrics.

Context inputs:

- TradingView charts (max three per week)
- price-based regime observations
- discretionary notes
- external information gathered manually

Context data is **never automated** and **never feeds execution directly**.

---

## 6. Review Integration

This data model feeds exactly three governance documents:

- `WEEKLY_RISK_CHECKLIST.md`
- `MONTHLY_RISK_REVIEW_TEMPLATE.md`
- `RISK_KERNEL_GOVERNANCE.md`

No other reviews are permitted.

---

## Invariants

- Data does not drive trades directly
- Reviews may reduce risk, never increase it
- Absence of data defaults to conservative behavior
- Flat is a valid and documented outcome
- Automation must not change this model

---

## Final Definition

If this data model is respected,  
the system remains controllable, auditable, and durable.
