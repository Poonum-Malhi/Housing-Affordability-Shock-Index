# Housing-Affordability-Shock-Index
The Housing Affordability Shock: How Europe's Cost of Living Crisis Became a Structural Economic Problem
#  Europe Under Pressure (Part 4)
## The Housing Affordability Shock Index (HASI)

> *"Real house prices stayed constant for a century — then surged. Rising land prices, not construction costs, explain 80% of the global housing boom."*
> — Knoll, Schularick & Steger (2017), American Economic Review

---

## What This Project Does

This notebook constructs a **Housing Affordability Shock Index (HASI)** for 16 EU countries and tests whether housing stress predicts unemployment — the fourth instalment of the *Europe Under Pressure* research series.

Housing unaffordability is not just a welfare concern. It is a **structural economic shock** that restricts labour mobility, depresses consumption, and drives a wedge between nominal wages and real living standards.

---

## Theoretical Backbone

| Paper | Key Finding |
|---|---|
| **Knoll, Schularick & Steger (2017)**, *AER* | Land prices (not construction costs) drive ~80% of the global housing boom since WWII |
| **IMF Working Paper (2023)** | Up to one-third of EU households projected to struggle with basic expenses by end-2023 |

---

## The Index: HASI

$$\text{HASI}_i = \frac{z(\text{Price-to-Income Ratio}_i) + z(\text{Overburden Rate}_i)}{2}$$

Two equally weighted, z-score normalised components:

| Component | Source | Code | Year |
|---|---|---|---|
| Price-to-Income Ratio | OECD Analytical House Price Database | HM1.2.1 | 2023 |
| Housing Cost Overburden Rate | Eurostat EU-SILC | `ilc_lvho07a` | 2023 |

**Price-to-Income Ratio**  nominal house prices ÷ disposable income per head, base 2015=100. A value of 150 means housing became 50% less affordable since 2015.

**Overburden Rate**  % of population spending more than 40% of income on housing (EU's official stress threshold).

---

##  Visualisations

| Figure | Description | Link |
|---|---|---|
| HASI Bar Chart | Country rankings by shock score | [View](fig1_HASI_bar.html) |
| Choropleth Map | Housing stress mapped across EU | [View](fig2_HASI_map.html) |
| Regression Scatter | HASI vs Unemployment with OLS line | [View](fig3_HASI_scatter.html) |

---

##  Regression Result

$$\text{Unemployment}_i = \alpha + \beta \cdot \text{HASI}_i + \varepsilon_i$$

| Statistic | Value |
|---|---|
| β (HASI coefficient) | –0.53 |
| p-value | 0.66 |
| R² | 0.014 |

The labour mobility trap hypothesis — that housing stress would raise unemployment — does not hold statistically. The negative β is consistent with Parts 1–3 of this series, reinforcing a recurring finding: **Europe's labour markets are resilient to structural shocks in ways simple theory does not predict.**

---

## Countries in Sample

Austria · Belgium · Czech Republic · Denmark · Finland · France · Germany · Greece · Hungary · Ireland · Italy · Netherlands · Poland · Portugal · Spain · Sweden

---

##  Series Overview

| Part | Shock | Key Paper |
|---|---|---|
| Part 1 | China Trade Shock | Autor, Dorn & Hanson (2013) |
| Part 2 | AI Automation Risk | Frey & Osborne (2017) |
| Part 3 | CBAM Climate Exposure | World Bank + Our World in Data |
| **Part 4** | **Housing Affordability** | **Knoll, Schularick & Steger (2017)** |

---

##  Tech Stack

`Python` · `Pandas` · `Statsmodels` · `Plotly` · `Jupyter` · `GitHub Pages`

---

##  References

- Knoll, K., Schularick, M., & Steger, T. (2017). No Price Like Home: Global House Prices, 1870–2012. *American Economic Review*, 107(2), 331–353.
- IMF (2023). European Housing Markets at a Turning Point. *IMF Working Paper* WP/23/76.
- OECD (2024). Analytical House Price Database. https://stats.oecd.org
- Eurostat (2024). Housing cost overburden rate, `ilc_lvho07a`. EU-SILC Survey.
- Eurostat (2024). Unemployment rate, `une_rt_a`.

---

*Part of the Europe Under Pressure research series — exploring structural economic shocks across the EU.*
-----
## Addendum — Panel Extension (July 2026)

The original analysis above tests a single-year cross-section (16 countries, 2023). This addendum
extends it to a full Eurostat panel to check whether the null result is robust to a larger sample.

### Methodology and a proxy substitution

The original HASI used the OECD price-to-income ratio, which is not readily available as a multi-year
pull. This extension substitutes the **Eurostat House Price Index** (`prc_hpi_a`) for it, an index of
the same underlying phenomenon (housing prices outpacing incomes) but not an identical measure. It is
combined with the same housing cost overburden rate (`ilc_lvho07a`), both z-scored within each year, and
regressed against unemployment (`une_rt_a`), 15 countries, 2005-2025.

### Results

| Specification | Coefficient | p-value | Observations |
|---|---|---|---|
| Single-year (2023, updated proxy) | -1.793 | 0.076 | 15 |
| Pooled OLS, no fixed effects | -0.993 | 0.266 | 243 |
| Two-way fixed effects panel | -0.415 | 0.541 | 243 |

### Interpretation

As with a companion extension of the China Shock analysis, expanding this sample to 243 country-year
observations does **not** produce significance, and adding fixed effects moves the result further from
significance. This is treated as a genuine null result rather than a null that merely reflects
insufficient statistical power in the original 16-country, single-year sample: the labour-mobility-trap
hypothesis is not supported even with a much larger panel.

### Data

Eurostat: House Price Index (`prc_hpi_a`, purchase=TOTAL, unit=I15_A_AVG), Housing cost overburden rate
(`ilc_lvho07a`, total population), Unemployment rate (`une_rt_a`, age 15-74, % of active population),
2005-2025.
