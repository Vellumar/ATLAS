# RISK_KERNEL_GOVERNANCE.md  

*Human-in-the-Loop Risk Governance — Single Source of Truth**

---

## 1. PURPOSE

This document defines the **Risk Kernel as a governance process**, not as software.

The Risk Kernel is the **highest authority** in the system.  
It decides **if**, **how much**, and **under what conditions** risk may be taken.

This file is the **single source of truth** for:

- portfolio risk limits,
- bot permissions,
- capital caps,
- pauses,
- escalation rules.

Automation is **explicitly out of scope** in Phase 1.

---

## 2. CORE PRINCIPLE

> **Risk decisions are made consciously, documented explicitly, and reviewed regularly.**

No bot, script, or model may:

- override the Risk Kernel,
- silently change risk,
- self-increase exposure.

Flat is a valid outcome.  
Inactivity is not failure.

---

## 3. ROLE DEFINITION

### 3.1 What the Risk Kernel IS

- A **decision authority**
- A **governance layer**
- A **manual control plane**
- A **documentation-first process**

### 3.2 What the Risk Kernel IS NOT

- Not a trading bot
- Not an optimizer
- Not a signal generator
- Not a prediction engine

---

## 4. CONTROLLED ENTITIES (RISK CONSUMERS)

The Risk Kernel governs all entities that **consume risk budget**:

| Entity                | Venue    | Risk Type                   |
| --------------------- | -------- | --------------------------- |
| Microstructure Alpha  | Bitfinex | Intraday BTC exposure       |
| Seasonal Trend Rider  | Alpaca   | Equity / ETF exposure       |
| RS Allocator Holdings | Bitfinex | BTC / XAUT / USD* exposure  |

Each entity is treated as:

- a **risk consumer**,
- with its own drawdown limits,
- and its own permission state.

---

## 5. GLOBAL SYSTEM STATES

The Risk Kernel assigns **one global state** at any time:

- `LIVE` – risk permitted within caps  
- `SHADOW` – analysis only, no new risk  
- `FLAT` – zero exposure enforced  
- `RECOVERY` – restricted, reduced risk  
- `PANIC` – emergency halt, manual intervention required  

**Rule:**  
If the global state is not `LIVE`, no entity may increase exposure.

---

## 6. RISK BUDGET MODEL (CONCEPTUAL)

### 6.1 Portfolio Risk Budget

- Total portfolio risk is capped absolutely.
- Drawdown caps are **hard**, not averaged.

### 6.2 Caps vs Targets

- **Caps** define the *maximum allowed exposure*.
- There are **no mandatory targets**.
- Actual exposure may be anywhere between `0` and `CAP`.

### 6.3 Multipliers (Manual in Phase 1)

- Multipliers are **human decisions**.
- They can only **reduce** caps, never increase them.
- Multipliers react to:
  - drawdowns,
  - instability,
  - behavioral issues (churn).

---

## 7. DRAWDOWN GOVERNANCE

### 7.1 Absolute Drawdown Limits

| Scope              | DD Hard Stop | Consequence        |
| ------------------ | ------------ | ------------------ |
| Portfolio          | 3.0%         | Immediate FLAT     |
| Micro Alpha        | 2.0%         | Shadow / Flat      |
| Seasonal Rider     | 1.5%         | Cooldown           |
| Allocator Holdings | 0.5%         | FLAT               |

Breaches are **immediate** and **non-negotiable**.

### 7.2 Post-Stop Behavior

- No instant re-entry
- Mandatory cooling-off period
- Written review required

---

## 8. STABLECOIN / CASH GOVERNANCE

### 8.1 USD* Definition

USD* is treated as a **risk-bearing instrument**, not cash.

It may include:

- fiat balances,
- stablecoins,
- exchange wallet balances.

### 8.2 Haircut Principle

Effective cash value is **discounted mentally**, not optimized.

If confidence in convertibility decreases:

- risk must be reduced,
- not compensated elsewhere.

---

## 9. SEASONAL & CALENDAR GOVERNANCE

### 9.1 Season Windows

Season windows define **eligibility**, not obligation.

They answer:
> “Is this strategy allowed to participate at all?”

They do not answer:
> “How much should be invested?”

### 9.2 Hard Calendar Pauses

- Year-end pause (24.12 – 02.01): FLAT
- Other pauses are discretionary and documented

---

## 10. DECISION RITUALS

### 10.1 Weekly Review (Light)

- Check DD per entity
- Check regime alignment
- Check behavioral issues
- Decide: continue / reduce / pause

### 10.2 Monthly Review (Formal)

- Review previous month decisions
- Evaluate stability, not PnL alone
- Set **caps and multipliers** for next month
- Document rationale

All decisions are written down.

---

## 11. DECISION LOGGING (MANDATORY)

Every Risk Kernel decision must record:

- date
- global state
- affected entities
- caps and multipliers
- reason for decision
- review date

No undocumented decisions.

---

## 12. INVARIANTS (CANNOT BE BROKEN)

- Risk is permissioned, not assumed
- Caps are ceilings, not goals
- Losses reduce freedom
- Stability precedes growth
- Flat is success
- Documentation precedes automation

---

## 13. ACCEPTANCE CRITERIA

The Risk Kernel is considered valid if:

- every exposure can be justified from this document,
- no bot can increase risk without explicit permission,
- all pauses and caps are explainable after the fact,
- removing automation does not break decision quality.

---

## FINAL DEFINITION

> **The Risk Kernel is a human-governed decision framework that controls when and how much risk the system is allowed to take, documented in Markdown and reviewed consciously.**
