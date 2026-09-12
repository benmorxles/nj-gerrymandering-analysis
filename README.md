[README.md](https://github.com/user-attachments/files/32139066/README.md)
# NJ Congressional Districts — Fairness Analysis

Companion code for *Analyzing Fairness in New Jersey's Congressional Districts: A Dive
into Speculated Partisan Gerrymandering with Math Modeling* (Benjamin Morales, Princeton
University).

## What's here

- **`NJ_Gerrymandering_Analysis.ipynb`** — the full analysis, runnable top to bottom.
  Computes district compactness (Polsby–Popper, Reock), population deviation, partisan
  metrics (efficiency gap, mean–median difference, partisan bias, seats–votes symmetry),
  and the demographic correlation analysis. Every figure and number in the paper is
  reproduced here.
- **`data/`** — bundled input data, each pulled directly from its primary source:
  - `population_demographics.csv` — NJ Congressional Redistricting Commission, *Population
    Summary Report* and *Population Demographics and Voting Age Report* (Dec. 2021,
    2020 Census, enacted 2022–2031 map)
  - `election_results_2022_us_house.csv` — NJ Division of Elections, certified 2022
    general election results, U.S. House (two-party totals)
  - `income_education_age.csv` — U.S. Census Bureau ACS 5-Year Estimates, 2022 vintage
    (Tables B19013, B15003, B01001)
- **`figures/`** — output figures, regenerated each time the notebook runs.

## Running it

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace NJ_Gerrymandering_Analysis.ipynb
```

The only network call is a one-time download of the Census Bureau's TIGER/Line
shapefile for NJ's enacted 118th-Congress districts (Section 1); everything else reads
from the bundled CSVs in `data/`.

## Why this exists

An earlier draft of this analysis accidentally mixed two different maps: district
geometry and race/ethnicity data were pulled from a 2020-vintage Census API query,
which — despite the "2020" label — returns pre-redistricting, 116th-Congress
boundaries, while income/education/age data were already on the correct, current
(118th-Congress) map. This repository fixes that by sourcing every input from the
same, correct, enacted 2022–2031 map, and documents each source's exact provenance so
the analysis can be independently checked and reproduced.
