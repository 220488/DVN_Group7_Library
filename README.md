# DVN Group 7 — Consumer Price Index, Australia

An interactive data visualisation dashboard exploring Australia's Consumer Price Index (CPI) trends across expenditure groups and capital cities (2024–2026).

Built for **36104 Data Visualisation** — Assessment Task 3, University of Technology Sydney.

---

## Project Overview

This project visualises ABS CPI data to help policymakers and the general public understand inflation patterns across Australia's eight capital cities and twelve expenditure categories.

**Key questions explored:**
- Which expenditure groups are driving inflation?
- How do price pressures differ across capital cities?
- How do analytical series (trimmed mean, weighted median) compare to headline CPI?

---

## Repository Structure

```
DVN_Group7_Library/
├── README.md                  # Project overview, setup, credits
├── docs/
│   └── DATA_DICTIONARY.md     # Variable definitions, types, and provenance
├── data/                      # Cleaned CSV files (derived from ABS releases)
├── src/                       # Streamlit application source code
└── .gitignore
```

---

## Getting Started

### Prerequisites

```bash
pip install streamlit pandas plotly
```

### Run the Dashboard

```bash
cd src
streamlit run app.py
```

---

## Dataset

| Field | Detail |
|---|---|
| **Source** | Australian Bureau of Statistics (ABS) |
| **Publication** | Consumer Price Index, Australia |
| **Catalogue No.** | 6401.0 |
| **Reference period** | June 2024 – February 2026 (monthly); quarterly historical |
| **Index reference** | September 2025 = 100.0 |
| **Geographic scope** | Weighted average of 8 capital cities (Sydney, Melbourne, Brisbane, Adelaide, Perth, Hobart, Darwin, Canberra) |
| **Licence** | [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) |
| **URL** | https://www.abs.gov.au/statistics/economy/price-indexes-and-inflation/consumer-price-index-australia/latest-release |

For full variable definitions, data types, units, and transformation notes, see [docs/DATA_DICTIONARY.md](docs/DATA_DICTIONARY.md).

---

## Credits

### Team — Group 7

| Name | Role | Responsibilities |
|---|---|---|
| Ying-Kai Liao (Kai) | Project Manager | Sprint planning, Gantt, syncs, pitch coordination, video submission |
| Desmond | Data Analyst | Dataset inspection, cleaning, wage join, headline findings, data validation |
| Jacky | Visual Designer | Palette, typography, wireframes, design system, accessibility audit |
| Kripa | Narrative Lead | Policymaker persona, narrative arc, tooltip copy, presenter coaching |
| Dhrishita | Dashboard Developer | Tool setup, dashboard build, advanced features, deployment |
| Shreeya | Deck & Pitch Lead | Slide deck, pitch structure, dry runs, rehearsal |
| Indigo Yufan Gong | Technical Documentarian | GitHub scaffolding, README, Data Dictionary, Credits, QA |

### Data Attribution

Australian Bureau of Statistics. (2026). *Consumer Price Index, Australia, February 2026* (Cat. No. 6401.0). ABS. https://www.abs.gov.au/statistics/economy/price-indexes-and-inflation/consumer-price-index-australia/latest-release

Licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).

---

## Licence

This project's code is released under the [MIT Licence](https://opensource.org/licenses/MIT).
Underlying ABS data is subject to [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
