# Design System — DVN Group 7: CPI Australia

**Visual Designer:** Jacky Wang (Chen-Tai Wang)  
**Tool:** Tableau Public  
**Version:** 1.0  
**Last Updated:** 2026-05-08  

---

## 1. Design Philosophy

This dashboard is designed for **cost-of-living policymakers and economic policy advisors**. The visual language prioritises clarity, credibility, and evidence-based storytelling over decoration.

**Design principles:**

- **Authority:** Colour and typography choices that convey institutional trust and analytical rigour.
- **Clarity:** Every visual element serves a purpose — no chartjunk, no gratuitous decoration.
- **Accessibility:** WCAG 2.1 AA compliant contrast ratios; colorblind-safe palettes throughout.
- **Narrative focus:** Visual hierarchy guides the reader through the What → So What → What Next arc.

---

## 2. Colour Palette

### 2.1 Core Palette

| Role | Name | Hex | Usage |
|------|------|-----|-------|
| **Primary** | Navy | `#1B3A5C` | Dashboard title, key labels |
| **Primary Light** | Slate Blue | `#3D6B99` | Secondary headings, highlights |
| **Background** | Off-White | `#FAFBFC` | Dashboard background |
| **Surface** | Light Grey | `#F0F2F5` | Filter pane, containers |
| **Text Primary** | Charcoal | `#1A1A2E` | Body text, chart titles |
| **Text Secondary** | Mid Grey | `#6B7280` | Captions, axis labels, annotations |
| **Border** | Pale Grey | `#D1D5DB` | Dividers, grid lines |

### 2.2 Semantic / Directional Colours

| Role | Name | Hex | Usage |
|------|------|-----|-------|
| **Inflation Up / Danger** | Vermillion | `#D64045` | Price increases, above-target inflation |
| **Positive / Easing** | Deep Teal | `#1A8A6E` | Declining trend, wages above CPI |
| **Warning / Caution** | Amber | `#E8910C` | Moderate pressure, watch-points |
| **Neutral Indicator** | Cool Grey | `#9CA3AF` | Baseline, no-change reference |

### 2.3 CPI vs WPI Comparison Pair

Used exclusively in Visual 1 (CPI vs WPI trend chart):

| Series | Hex | Rationale |
|--------|-----|-----------|
| **CPI (Inflation)** | `#D64045` | Red = cost pressure |
| **WPI (Wages)** | `#3D6B99` | Blue = income/institutional |

### 2.4 City Palette (8 Capital Cities)

ColorBrewer "Dark2", colorblind-safe (Deuteranopia, Protanopia tested):

| City | Hex |
|------|-----|
| Sydney | `#1B9E77` |
| Melbourne | `#D95F02` |
| Brisbane | `#7570B3` |
| Adelaide | `#E7298A` |
| Perth | `#66A61E` |
| Hobart | `#E6AB02` |
| Darwin | `#A6761D` |
| Canberra | `#666666` |

**Rule:** When only a subset of cities is shown, use the same assigned colour — never reassign.

### 2.5 Expenditure Group Palette (11 Categories)

| Group | Hex |
|-------|-----|
| Food & non-alcoholic beverages | `#4E79A7` |
| Alcohol & tobacco | `#A0CBE8` |
| Clothing & footwear | `#F28E2B` |
| **Housing** | `#D64045` |
| Furnishings & household equipment | `#76B7B2` |
| Health | `#59A14F` |
| Transport | `#EDC948` |
| Communication | `#B07AA1` |
| Recreation & culture | `#FF9DA7` |
| Education | `#9C755F` |
| Insurance & financial services | `#BAB0AC` |

Note: Housing uses Vermillion (`#D64045`) to align with the narrative emphasis on housing as the key pressure point.

### 2.6 Heatmap Diverging Scale

7-stop diverging scale from Teal (easing) through Off-White (neutral) to Vermillion (pressure):

`#1A8A6E` → `#7EC4AA` → `#C5E5D6` → `#FAFBFC` → `#F0A8AA` → `#E06E72` → `#D64045`

---

## 3. Typography

### 3.1 Font Selection

| Element | Font | Size | Weight | Colour |
|---------|------|------|--------|--------|
| Dashboard Title | Tableau Bold | 22pt | Bold | `#1B3A5C` Navy |
| Sheet Title | Tableau Book | 14pt | Bold | `#1A1A2E` Charcoal |
| Axis Title | Tableau Book | 10pt | Regular | `#6B7280` Mid Grey |
| Axis Tick Labels | Tableau Book | 9pt | Regular | `#6B7280` Mid Grey |
| Tooltip Header | Tableau Bold | 11pt | Bold | `#1A1A2E` Charcoal |
| Tooltip Body | Tableau Book | 10pt | Regular | `#1A1A2E` Charcoal |
| Annotation | Tableau Book | 9pt | Regular | `#6B7280` Mid Grey |
| Source Attribution | Tableau Light | 8pt | Italic | `#9CA3AF` Cool Grey |

### 3.2 Text Formatting Rules

- Chart titles: **sentence case** (e.g., "Are wages keeping pace with inflation?")
- Axis labels: **Title Case** (e.g., "Annual % Change")
- No ALL CAPS except short abbreviations (CPI, WPI)
- Numbers: one decimal for percentages (3.2%), no decimal for index values

---

## 4. Tableau Implementation

### 4.1 Custom Palettes — Preferences.tps

A `src/Preferences.tps` file is provided. To use:

1. Close Tableau Desktop
2. Copy `src/Preferences.tps` to your **My Tableau Repository** folder (usually `Documents/My Tableau Repository/`)
3. Reopen Tableau — the following palettes will appear under "Select Color Palette":
   - **DVN CPI vs WPI** — 2 colours for CPI/WPI comparison
   - **DVN Semantic** — 4 colours for directional indicators
   - **DVN Capital Cities** — 8 colours for city comparisons
   - **DVN Expenditure Groups** — 11 colours for expenditure categories
   - **DVN Heatmap Diverging** — 7-stop diverging scale

### 4.2 Dashboard Formatting

| Setting | Value |
|---------|-------|
| Dashboard background | `#FAFBFC` |
| Sheet background | None (transparent) |
| Grid lines | Thin, `#E5E7EB` |
| Axis rulers | `#D1D5DB` |
| Zero lines | Dashed, `#9CA3AF` |
| Borders between sheets | None or `#D1D5DB` thin |
| Tooltip background | White |
| Filter pane background | `#F0F2F5` |

### 4.3 Worksheet Naming Convention

| Worksheet | Name |
|-----------|------|
| Visual 1 | `V1_CPI_vs_WPI_Trend` |
| Visual 2 | `V2_City_CPI_Comparison` |
| Visual 3 | `V3_Expenditure_Category_Ranking` |
| Visual 4 | `V4_Pressure_Heatmap` |

### 4.4 Line & Mark Sizing

| Mark Type | Size |
|-----------|------|
| Primary line (CPI, WPI) | 2.5pt |
| Secondary lines (city comparison) | 2pt |
| Reference / baseline line | 1pt, dashed |
| Bar charts | Automatic, no mark borders |
| Tooltips | Show on hover |

---

## 5. Chart-Specific Guidelines

### Visual 1: Are wages keeping pace with inflation?

- Chart type: Dual-line chart
- Palette: **DVN CPI vs WPI**
- CPI = `#D64045`, WPI = `#3D6B99`
- Add reference line at 0% if showing YoY change
- Annotate key crossover points

### Visual 2: How does inflation pressure differ across Australian capital cities?

- Chart type: Multi-line or small multiples
- Palette: **DVN Capital Cities**
- Consistent colour assignment per city across all views
- Legend position: top, horizontal

### Visual 3: Which household costs are rising the fastest?

- Chart type: Horizontal bar chart, sorted descending
- Palette: **DVN Expenditure Groups**
- Housing bar stands out (same red as "Inflation Up")
- Labels on bar ends

### Visual 4: Where is affordability pressure most concentrated?

- Chart type: Heatmap (City × Category)
- Palette: **DVN Heatmap Diverging**
- Cell labels: show percentage values
- Sort rows/columns by severity

---

## 6. Accessibility Checklist

| Requirement | Standard | Status |
|-------------|----------|--------|
| Text contrast (normal text) | ≥ 4.5:1 (WCAG AA) | ✅ Charcoal on Off-White = 15.8:1 |
| Text contrast (captions) | ≥ 4.5:1 (WCAG AA) | ✅ Mid Grey on Off-White = 5.0:1 |
| Chart colours (adjacent) | Distinguishable under Deuteranopia & Protanopia | ⬜ To verify post-deployment |
| Alt text for each visual | Descriptive title + caption in Tableau | ⬜ To add |
| Tooltip readability | Sufficient font size, clear hierarchy | ⬜ To verify post-deployment |

Full accessibility audit: `docs/ACCESSIBILITY_AUDIT.md` (after dashboard deployment).

---

## 7. Source Attribution

Every dashboard view should include:

> Source: ABS Consumer Price Index, Australia (Cat. No. 6401.0); ABS Wage Price Index (Cat. No. 6345.0).

Style: 8pt, `#9CA3AF`, italic. Positioned at the bottom of the dashboard.

---

## 8. File References

| File | Location | Purpose |
|------|----------|---------|
| Tableau palette | `src/Preferences.tps` | Custom colour palettes for Tableau Desktop |
| This document | `docs/DESIGN_SYSTEM.md` | Single source of truth for all visual decisions |
| Accessibility audit | `docs/ACCESSIBILITY_AUDIT.md` | Post-deployment accessibility review |

---

## 9. Revision Log

| Date | Version | Change | Author |
|------|---------|--------|--------|
| 2026-05-08 | 1.0 | Initial design system (Tableau) | Jacky Wang |
