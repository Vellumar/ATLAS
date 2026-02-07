# TRADING_SYSTEM_OVERVIEW.md

## Purpose

This document provides a **single-page overview** of the complete trading system.

It defines:

- which bots exist,
- where they trade,
- what they trade,
- and what role each bot has.

This file is the **entry point** for humans and LLMs.

---

## System Overview

The system consists of **three independent but coordinated trading bots**.
Each bot has a **strictly separated role**.

---

## Bot Portfolio

| Bot Name | Internal Code| Venue     | Assets                        | Timeframe        | Role                          | Activity Pattern                | DD Hard Stop |
| -------  | -------------| --------- | ----------------------------- | ---------------- | ----------------------------- | ------------------------------- | ------------ |
| STRATUM  | Micro Alpha  | Bitfinex  | BTC Perpetual + BTC Spot      | 15s / 30s / 5m   | Intraday Microstructure Alpha | Daily during liquid sessions    | 2.0%         |
| ORBIT    | Seasonal     | Alpaca    | QQQ, SPY, XLU, XLP, GLD, BIL  | 4h / 1h / 15m    | Regime Participation          | Seasonal (Sep–Dec, Jan–May)     | 1.5%         |
| ANCHOR   | Risk Kernel  | Bitfinex  | BTC, XAUT, USD*               | 4h / Daily       | Risk Control + Allocation     | Monthly decisions               | 0.5%         |

USD* = Fiat or stablecoin exposure, treated as risk-bearing and haircut-adjusted.

---

## Role Separation (Invariant)

- **STRATUM** generates short-term alpha only.
- **ORBIT** participates in higher-level regimes only.
- **ANCHOR** controls risk and allocation across the entire system.

No bot:

- predicts markets,
- overrides another bot,
- or increases risk autonomously.

---

## Control Hierarchy

1. **ANCHOR** (Risk Kernel)  
   - Sets caps, permissions, and global states  
   - Can reduce or stop all other bots  

2. **ORBIT** (Seasonal Regime Bot)  
   - Trades only when eligible by season and price regime  

3. **STRATUM** (Intraday Alpha Bot)  
   - Trades continuously but is always risk-limited  

---

## Design Principles

- Risk is permissioned, not assumed
- Caps are ceilings, not targets
- Flat is a valid and successful state
- Stability precedes growth
- Documentation precedes automation

---

## Canonical Documents

This system is governed by the following documents:

1. `RISK_KERNEL_GOVERNANCE.md`
2. `MONTHLY_RISK_REVIEW_TEMPLATE.md`
3. `WEEKLY_RISK_CHECKLIST.md`

This file is descriptive only and contains **no decision logic**.

---

## Final Note

If this document is understood,  
the entire trading system is understood.
