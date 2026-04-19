# Data Dictionary

**Project:** DVN Group 7 — Consumer Price Index, Australia  
**Maintained by:** Indigo Yufan Gong (Technical Documentarian)  
**Last updated:** 2026-04-20  

---

## Source

| Field | Detail |
|---|---|
| **Publisher** | Australian Bureau of Statistics (ABS) |
| **Publication title** | Consumer Price Index, Australia |
| **Catalogue number** | 6401.0 |
| **Latest release** | February 2026 (released 25 March 2026) |
| **Access URL** | https://www.abs.gov.au/statistics/economy/price-indexes-and-inflation/consumer-price-index-australia/latest-release |
| **Licence** | Creative Commons Attribution 4.0 International (CC BY 4.0) |
| **Index reference period** | September 2025 = 100.0 |

---

## 1. Core CPI Variables

| Variable Name | Type | Unit | Description | Source Column / Series | Notes |
|---|---|---|---|---|---|
| `period` | date | YYYY-MM (monthly) or YYYY-Qq (quarterly) | Reference period for the observation | ABS Table headers | Converted to `datetime` on load |
| `city` | string | — | One of eight capital cities, or `All Cities` (weighted average) | ABS geographic dimension | Values: `Sydney`, `Melbourne`, `Brisbane`, `Adelaide`, `Perth`, `Hobart`, `Darwin`, `Canberra`, `All Cities` |
| `expenditure_group` | string | — | One of 12 ABS expenditure groups, or `All Groups` (headline CPI) | ABS row dimension | See Section 2 for full list |
| `index_value` | float | Index points (Sep 2025 = 100.0) | CPI index level for a given period, city, and group | ABS published index number | Re-referenced to Sep 2025 = 100.0 |
| `change_monthly_pct` | float | Percentage (%) | Month-on-month change in index value | Derived | Calculated as `(index_value / index_value.shift(1) - 1) * 100` |
| `change_annual_pct` | float | Percentage (%) | Year-on-year change in index value | Derived | Calculated as `(index_value / index_value.shift(12) - 1) * 100` for monthly series |
| `change_quarterly_pct` | float | Percentage (%) | Quarter-on-quarter change | Derived | Calculated as `(index_value / index_value.shift(1) - 1) * 100` on quarterly series |
| `seasonally_adjusted` | boolean | — | Whether the observation is seasonally adjusted | ABS series flag | `True` for SA series; `False` for original |

---

## 2. Expenditure Groups

The ABS defines 12 expenditure groups that make up the headline CPI basket.

| Code | Group Name | Description |
|---|---|---|
| `G01` | Food and non-alcoholic beverages | Groceries, fresh produce, restaurant meals |
| `G02` | Alcohol and tobacco | Alcoholic drinks, tobacco products |
| `G03` | Clothing and footwear | Garments, shoes, accessories |
| `G04` | Housing | Rent, new dwelling purchases, utilities (electricity, gas, water) |
| `G05` | Furnishings and household equipment | Furniture, appliances, household tools |
| `G06` | Health | Medical services, pharmaceuticals, hospital costs |
| `G07` | Transport | Automotive fuel, vehicle purchase, public transport fares |
| `G08` | Communication | Phone plans, internet services, postal |
| `G09` | Recreation and culture | Entertainment, travel, sport, arts |
| `G10` | Education | Tuition fees, childcare |
| `G11` | Insurance and financial services | Home/car/health insurance, bank fees |
| `G12` | Alcohol and tobacco *(see G02)* | — |

---

## 3. Analytical Series Variables

These are additional ABS series used to measure underlying inflation, stripping out volatile items.

| Variable Name | Type | Unit | Description | Source | Notes |
|---|---|---|---|---|---|
| `trimmed_mean` | float | % change (annual or monthly) | Average CPI after removing the top and bottom 15% of price changes by weight | ABS analytical series | Smooths out extreme movements; preferred by RBA |
| `weighted_median` | float | % change (annual or monthly) | The midpoint of the CPI weight distribution | ABS analytical series | More robust to outliers than headline CPI |
| `tradables_pct` | float | % change | Price change for goods and services exposed to international competition | ABS analytical series | Reflects global supply/demand pressures |
| `non_tradables_pct` | float | % change | Price change for domestic goods and services | ABS analytical series | Reflects domestic cost pressures |
| `goods_pct` | float | % change | Price change for physical goods | ABS analytical series | — |
| `services_pct` | float | % change | Price change for services | ABS analytical series | — |
| `discretionary_pct` | float | % change | Price change for non-essential spending | ABS analytical series | — |
| `non_discretionary_pct` | float | % change | Price change for essential spending | ABS analytical series | — |

---

## 4. Derived / Engineered Variables

Variables created during data cleaning and analysis (not directly from ABS releases).

| Variable Name | Type | Unit | Description | Created by | Script Reference |
|---|---|---|---|---|---|
| `is_rebate_affected` | boolean | — | Flags periods where government electricity rebates distort the Housing group CPI | Desmond | `src/clean.py` |
| `electricity_ex_rebate_pct` | float | % change | Electricity price change excluding the effect of government rebates | Desmond | `src/clean.py` |
| `city_rank` | integer | — | Rank of city by annual CPI change within a given period (1 = highest inflation) | Desmond | `src/clean.py` |

---

## 5. Data Collection Methods (ABS)

The ABS collects CPI data through:

- **Web-scraping** of retail and service provider websites
- **Online and telephone retailer collections**
- **Supermarket scanner data** (administrative data)
- **Survey collections** for items not available digitally

---

## 6. Known Limitations & Caveats

| Issue | Detail |
|---|---|
| Electricity rebate distortion | Federal and state government electricity rebates from Jul 2025 significantly suppress the Housing group and headline CPI. Figures excluding rebates are provided in the analytical series. |
| Monthly series start date | Monthly CPI series only begins June 2024. Prior data is quarterly only. |
| Index re-referencing | ABS re-referenced the index to Sep 2025 = 100.0. Comparisons to pre-re-reference data require conversion factors (available in ABS appendices). |
| Capital city scope | Data covers only the eight state/territory capital cities. Regional and rural price movements are not captured. |

---

## 7. Citation

> Australian Bureau of Statistics. (2026). *Consumer Price Index, Australia, February 2026* (Cat. No. 6401.0). Commonwealth of Australia. https://www.abs.gov.au/statistics/economy/price-indexes-and-inflation/consumer-price-index-australia/latest-release
>
> Licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).
