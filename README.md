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
