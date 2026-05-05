# Mortgage Loan Panel — Dataset Card

---

## Overview

| | |
|---|---|
| Borrowers | 50,000 |
| Periods | 60 |
| Variables | 23 |
| Structure | Panel (longitudinal) |

Loans may originate before the observation window begins and may be censored at maturity or refinancing. Periods are deidentified.

---

## Variables

### Identifiers & time

| Variable | Description |
|---|---|
| `id` | Borrower ID |
| `time` | Time stamp of observation |
| `orig_time` | Time stamp of loan origination |
| `first_time` | Time stamp of first observation |
| `mat_time` | Time stamp of maturity |

### Time-varying (at observation)

| Variable | Description |
|---|---|
| `balance_time` | Outstanding balance |
| `LTV_time` | Loan-to-value ratio (%) |
| `interest_rate_time` | Interest rate (%) |
| `hpi_time` | House price index (base year = 100) |
| `gdp_time` | GDP growth (%) |
| `uer_time` | Unemployment rate (%) |

### Fixed at origination

| Variable | Description |
|---|---|
| `REtype_CO_orig_time` | Real estate type: condominium (1/0) |
| `REtype_PU_orig_time` | Real estate type: planned urban development (1/0) |
| `REtype_SF_orig_time` | Real estate type: single-family home (1/0) |
| `investor_orig_time` | Investor borrower (1/0) |
| `balance_orig_time` | Outstanding balance at origination |
| `FICO_orig_time` | FICO credit score |
| `LTV_orig_time` | Loan-to-value ratio (%) |
| `Interest_Rate_orig_time` | Interest rate (%) |
| `hpi_orig_time` | House price index at origination (base year = 100) |

### Outcome variables

| Variable | Description |
|---|---|
| `default_time` | Default event at observation time (1/0) |
| `payoff_time` | Payoff event at observation time (1/0) |
| `status_time` | Loan status: 0 = active, 1 = default, 2 = payoff |

---

## Notes

- The dataset is in **panel form**: each borrower (`id`) appears across multiple time periods.
- `orig_time` can be negative, indicating the loan originated before the dataset observation window.
- Macro variables (`gdp_time`, `uer_time`, `hpi_time`) vary over time but not across borrowers within the same period.
- Property type is one-hot encoded across three mutually exclusive columns (`CO`, `PU`, `SF`).
