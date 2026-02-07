# ATLAS SYSTEM_MASTER.md

## Purpose

This document defines the **ATLAS trading system** at a structural level.

It describes:

- which trading systems exist,
- what each system trades,
- how risk is governed,
- and which invariants must never be violated.

This file is the **single canonical reference** for humans and LLMs.

---

## System Summary

ATLAS consists of **three independent trading systems** with **strict role separation**, governed by a **human Risk Kernel**.

There is:

- one intraday alpha engine,
- one seasonal regime participant,
- one long-horizon allocation system,
- and one external risk authority.

No trading system predicts markets.  
No trading system increases risk autonomously.

---

## Trading Systems

| System Name | Codename | Venue    | Assets                       | Timeframe        | Primary Role                  | Activity Pattern            | DD Hard Stop |
| ----------- | -------- | -------- | ---------------------------- | ---------------- | ----------------------------- | --------------------------- | ------------ |
| STRATUM     | Alpha    | Bitfinex | BTC Perpetual, BTC Spot      | 15s / 30s / 5m   | Intraday Microstructure Alpha | Daily, session-based        | 2.0%         |
| ORBIT       | Seasonal | Alpaca   | QQQ, SPY, XLU, XLP, GLD, BIL | 4h / 1h / 15m    | Seasonal Regime Participation | Seasonal (Sep–Dec, Jan–May) | 1.5%         |
| ANCHOR      | Alloc    | Bitfinex | BTC, XAUT, USD*              | 4h / Daily       | Long-Horizon Allocation       | Monthly decisions           | 0.5%         |

USD* refers to fiat or stablecoin exposure and is treated as risk-bearing.

---

## Role Definitions

### STRATUM

- Generates short-term intraday alpha
- Uses microstructure and order flow
- Has no awareness of portfolio-level risk
- Can be reduced or stopped at any time

STRATUM never decides allocation.

---

### ORBIT

- Participates in higher-level market regimes
- Is active only during explicit seasonal windows
- Uses price-derived regime filters only
- Does not trade continuously

ORBIT has eligibility, not entitlement.

---

### ANCHOR

- Trades slow, structural allocation
- Allocates between BTC, XAUT, and USD*
- Operates on multi-day to monthly horizons
- Has its own drawdown constraints

ANCHOR is a trading system, not a governance authority.

---

## Risk Kernel Definition

The Risk Kernel is not a trading system and not automated code.

It is a human-governed authority that:

- sets global operating states (LIVE, SHADOW, FLAT, PANIC),
- defines exposure caps for all trading systems,
- enforces hard drawdown stops,
- and reviews system behavior on a weekly and monthly basis.

The Risk Kernel is implemented through:

- human decision-making (the operator),
- structured analysis (LLM-assisted reports),
- and documented governance protocols.

All trading systems are subjects of the Risk Kernel.  
No system may override, bypass, or reinterpret its constraints.

---

## Control Hierarchy

1. Risk Kernel (Human Governance)
   - Sets global state
   - Defines caps
   - Enforces drawdown limits

2. ANCHOR
   - Allocates capital within permitted bounds

3. ORBIT
   - Trades only if eligible and permitted

4. STRATUM
   - Trades continuously within strict limits

If the Risk Kernel is not `LIVE`, no system may increase exposure.

---

## Global Risk Model

- Risk is permissioned, not assumed
- Exposure is controlled via caps, not targets
- Losses reduce future freedom
- Flat is a valid and successful state

Absolute drawdown limits exist at:

- portfolio level,
- system level.

All drawdown stops are hard.

---

## Design Invariants

The following rules must never be broken:

- No trading system may increase risk autonomously
- No trading system may override another
- Governance is external to execution
- Caps are ceilings, not goals
- Stability precedes growth
- Documentation precedes automation

---

## Operating Model

- Decisions are human-governed
- Analysis is price-derived
- Automation is optional and secondary
- All decisions must be explainable after the fact

---

## Canonical Governance Documents

This system is governed operationally by:

- `RISK_KERNEL_GOVERNANCE.md`
- `MONTHLY_RISK_REVIEW_TEMPLATE.md`
- `WEEKLY_RISK_CHECKLIST.md`

Those documents implement this master definition.

---

## Final Definition

If this document is understood,  
the entire ATLAS trading system is understood.
