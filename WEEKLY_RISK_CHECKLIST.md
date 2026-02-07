# WEEKLY_RISK_CHECKLIST.md

## Risk Kernel Weekly Stability and Discipline Check

---

## 1. Purpose

This document defines the weekly risk check ritual.

It is not a performance review.  
It is a discipline, stability, and permission check.

The weekly review answers one question only:

Is the system still behaving in a way that deserves risk?

Time required: 10–15 minutes.

---

## 2. Core Principles

- Weekly checks never increase risk
- Weekly checks may only maintain or reduce risk
- Drawdown discipline overrides opportunity
- Flat is always acceptable
- No optimization mid-month

---

## 3. Review Period

- Review Week: `YYYY-WW`
- Review Date: `YYYY-MM-DD`

---

## 4. Global System Status

| Item                   | Status                         | Comment |
| ---------------------- | ------------------------------ | ------- |
| Global State           | LIVE / RECOVERY / FLAT / PANIC |         |
| Portfolio DD Current   |                                |         |
| Portfolio DD Weekly    |                                |         |
| Any Hard Stop Hit      | Yes / No                       |         |

Decision:

- ☐ Continue as-is
- ☐ Tighten risk
- ☐ Force FLAT

---

## 5. Bot Health Check

### 5.1 Microstructure Alpha (Bitfinex)

| Check Item                | Status  | Comment |
| ------------------------- | ------- | ------- |
| DD Within Limits          | Yes / No|         |
| Kill Switch Triggered     | Yes / No|         |
| Shadow or Flat Activated  | Yes / No|         |
| Overtrading Detected      | Yes / No|         |
| Session Discipline Intact | Yes / No|         |

Weekly Action:

- ☐ No change
- ☐ Reduce cap or multiplier
- ☐ Force SHADOW
- ☐ Force FLAT

---

### 5.2 Seasonal Trend Rider (Alpaca)

| Check Item               | Status  | Comment |
| ------------------------ | ------- | ------- |
| Regime Alignment Intact  | Yes / No|         |
| Gate Discipline Intact   | Yes / No|         |
| Cooldown Triggered       | Yes / No|         |
| Churn Observed           | Yes / No|         |
| Exposure Appropriate     | Yes / No|         |

Weekly Action:

- ☐ No change
- ☐ Reduce cap or multiplier
- ☐ Force CASH
- ☐ Suspend for remainder of month

---

### 5.3 RS Allocator Holdings (Bitfinex)

| Check Item                    | Status  | Comment |
| ----------------------------- | ------- | ------- |
| Allocator DD Within Limit     | Yes / No|         |
| Asset Mix Unchanged           | Yes / No|         |
| Stablecoin Integrity Intact   | Yes / No|         |
| USD Concentration Acceptable  | Yes / No|         |

Weekly Action:

- ☐ No change
- ☐ Reduce allocator exposure
- ☐ Increase CASH bias
- ☐ Force FLAT

---

## 6. Calendar and Event Check

| Item                     | Status                    | Comment |
| ------------------------ | ------------------------- | ------- |
| Major Events Ahead       | Yes / No                  |         |
| Holiday or Low Liquidity | Yes / No                  |         |
| Seasonal Window          | Active / Neutral / Ending |         |

Action Required:

- ☐ None
- ☐ Tighten caps
- ☐ Temporary pause

---

## 7. Caps and Multipliers Weekly View

| Entity               | Current Cap | Multiplier | Effective Risk |
| -------------------- | ----------- | ---------- | -------------- |
| Microstructure Alpha |             |            |                |
| Seasonal Rider       |             |            |                |
| RS Allocator         | Base Only   |            |                |

Rule:
Weekly review may only decrease effective risk.

---

## 8. Behavioral Red Flags

Check any that apply:

- ☐ Emotional decision pressure
- ☐ Desire to recover losses
- ☐ Ignoring flat signals
- ☐ Strategy drift
- ☐ Undocumented manual overrides

If any are checked, tighten risk immediately.

---

## 9. Weekly Decision Summary

- Global state for coming week:
- Bots under restriction:
- Overrides applied:
- Reasoning:

---

## 10. Sign-Off

- Reviewer:
- Date:
- Confidence Level: Low / Medium / High

---

## 11. Final Validation Checklist

- ☐ No risk increase occurred
- ☐ All drawdown limits respected
- ☐ Overrides documented
- ☐ Flat considered a valid outcome

---

Reminder:
Weekly reviews protect capital.  
Capital protection enables longevity.
