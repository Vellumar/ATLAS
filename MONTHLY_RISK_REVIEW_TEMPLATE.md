# MONTHLY_RISK_REVIEW_TEMPLATE.md

*Risk Kernel — Monthly Governance & Allocation Review**

---

## 1. PURPOSE

This document defines the **monthly risk review ritual**.

Its goal is **not optimization** and **not forecasting**.  
Its goal is **capital preservation, stability assessment, and permission setting** for the next month.

This file is filled out **once per month** and archived.

---

## 2. CORE PRINCIPLES

- Monthly decisions set **CAPS**, never targets
- Risk may only be **maintained or reduced**, never increased reactively
- Promotions require **stability**, not high returns
- Losses reduce freedom
- Flat is a valid decision

---

## 3. REVIEW PERIOD

- **Review Month:** `YYYY-MM`
- **Review Date:** `YYYY-MM-DD`
- **Next Review Date:** `YYYY-MM-DD`

---

## 4. GLOBAL PORTFOLIO STATUS

### 4.1 Portfolio Overview

| Metric                 | Value                         | Comment |
| ---------------------- | ----------------------------- | ------- |
| Start NAV              |                               |         |
| End NAV                |                               |         |
| Monthly Return         |                               |         |
| Max Portfolio DD       |                               |         |
| Global State End-Month | LIVE, RECOVERY, FLAT, or PANIC|         |

### 4.2 Portfolio Risk Assessment

- Was any **portfolio hard stop** approached or breached?
  - ☐ No
  - ☐ Yes → explain:

- Did the portfolio spend time in `FLAT`, `RECOVERY`, or `PANIC`?
  - ☐ No
  - ☐ Yes → describe duration and reason:

---

## 5. BOT-LEVEL REVIEW (RISK CONSUMERS)

### 5.1 Microstructure Alpha (Bitfinex)

| Metric             | Value                    | Comment |
| ------------------ | ------------------------ | ------- |
| Monthly Return     |                          |         |
| Max DD             |                          |         |
| Kill-Switch Hit    | Yes / No                 |         |
| Shadow / Flat Time |                          |         |
| Behavioral Issues  | None / Churn / Other     |         |

**Assessment:**

- ☐ Stable
- ☐ Needs reduction
- ☐ Suspend next month

---

### 5.2 Seasonal Trend Rider (Alpaca)

| Metric            | Value                      | Comment |
| ----------------- | -------------------------- | ------- |
| Monthly Return    |                            |         |
| Max DD            |                            |         |
| Cooldown Triggered| Yes / No                   |         |
| Regime Alignment  | Good / Neutral / Poor      |         |
| Gate Discipline   | Good / Weak                |         |

**Assessment:**

- ☐ Stable
- ☐ Reduce cap
- ☐ Suspend next month

---

### 5.3 RS Allocator Holdings (Bitfinex)

| Metric                | Value          | Comment |
| --------------------- | -------------- | ------- |
| Asset Mix             |                |         |
| Max DD                |                |         |
| Stablecoin Share (%)  |                |         |
| USD* Integrity Issues | Yes / No       |         |

**Assessment:**

- ☐ Stable
- ☐ Reduce allocator exposure
- ☐ Force CASH bias

---

## 6. SEASONAL CONTEXT (ELIGIBILITY ONLY)

| Period        | Season Type | Notes |
| ------------- | ----------- | ----- |
| Current Month |             |       |
| Next Month    |             |       |

Season windows **only define eligibility**, not allocation.

---

## 7. CAPS FOR NEXT MONTH (UPPER BOUNDS)

| Entity               | Seasonal Cap | Multiplier | Final Allowed Cap |
| -------------------- | ------------ | ---------- | ----------------- |
| Microstructure Alpha |              |            |                   |
| Seasonal Rider       |              |            |                   |
| RS Allocator         | Base Only    |            |                   |

**Rules:**

- Multipliers ∈ `[0.0 – 1.0]`
- Multipliers may only be reduced after instability
- Increases require **multiple stable months**

---

## 8. GLOBAL STATE FOR NEXT MONTH

Select exactly one:

- ☐ `LIVE`
- ☐ `RECOVERY`
- ☐ `FLAT`
- ☐ `PANIC`

**Rationale:**

---

## 9. PAUSES & OVERRIDES

- Year-end pause applicable next month? ☐ Yes / ☐ No
- Event-based restrictions? ☐ Yes / ☐ No

If yes, specify:

---

## 10. KEY RISKS IDENTIFIED

List **at most three** dominant risks for the coming month:

1.
2.
3.

---

## 11. DECISIONS SUMMARY (ONE PAGE)

- Approved entities for next month:
- Entities under restriction:
- Max portfolio risk stance:
- Exceptional notes:

---

## 12. SIGN-OFF

- **Decision Maker:**
- **Date:**
- **Confidence Level:** Low / Medium / High

---

## FINAL CHECK (MUST PASS)

- ☐ No cap was increased after losses
- ☐ All DD breaches were respected
- ☐ All decisions are explainable without PnL justification
- ☐ Flat was considered a valid option
