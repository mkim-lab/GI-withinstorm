# Optimal Green Infrastructure Placement and Within-Storm Variability

This repository contains the plotting notebooks and numerical results for:

> **Nam, S. and Kim, M.** (2026). Everything Comes Down to Timing: Optimal Green Infrastructure Placement and The Effect of Within-Storm Variability.

## Repository contents

### Notebooks

| File | Description |
|------|-------------|
| `empirical_analysis.ipynb` | Observed-event figures (Figures 2, 5, 8). Cell 1: rainfall histograms. Cell 2: regime diagram with event scatter colored by optimal subcatchment. Cells 3--5: location-change ratios and regret statistics by storm characteristic. |
| `analytical_framework.ipynb` | Analytical figures (Figures 3, 4, 6, 7). Cell 1: hydrograph decomposition showing rainfall, routing response, and weighted product per subcatchment (Figure 6 with uniform file, Figure 7 with Beta files). Cell 2: $3 \times 3$ dominant-region maps (Figure 4). Cell 3: stacked and line hydrographs before/after GI for four rainfall patterns (Figure 3). |

### Observed rainfall data

| File | Description |
|------|-------------|
| `BusanRainfall Results.xlsx` | 2,351 hourly storm events (Busan KMA) evaluated at three virtual catchment scales ($t_n = 0.5, 2, 5$ h; 7,053 rows total). Columns: rainfall descriptors, fitted Beta parameters with goodness-of-fit metrics, $(T_r, T_n)$, peak-reduction performance under actual and uniform hyetographs, optimal subcatchment labels, and absolute/relative regret. |

### Subcatchment-level responses

Each file has a `meta` sheet (case parameters: $T_r$, $T_n$, $S_\text{eq}$, Beta shape, fill/peak times, $\tilde{R}$ per subcatchment) and per-case time-series sheets for the rainfall pattern and the routing response at each subcatchment.

| File | Description |
|------|-------------|
| `Rainfall Results(Uniform).xlsx` | Three cases under constant rainfall at representative $(T_r, T_n)$ points. |
| `Rainfall Results(Beta rainfall-Concentration).xlsx` | Three cases varying $\kappa = 3, 10, 30$ at fixed mode $= 0.1$. |
| `Rainfall Results(Beta rainfall-Peak position).xlsx` | Three cases varying mode $= 0.1, 0.5, 0.9$ at fixed $\kappa = 3$. |

### Outlet responses

Each file has pre-computed outlet hydrographs (no-GI baseline + GI at each subcatchment) for four rainfall patterns (constant, linearly decreasing, linearly increasing, triangular) at a specific routing kernel and $(T_r, T_n)$. Sheets contain bypass/GI-modified flows, total outflow, and peak-reduction statistics. Time steps vary by simulation duration (~14,400 for $T_r{=}2, T_n{=}6$; ~4,800 for $T_r{=}3, T_n{=}2$).

| Routing kernel | $T_r=2, T_n=6$ | $T_r=3, T_n=2$ | $T_r=3, T_n=4$ |
|----------------|-----------------|-----------------|-----------------|
| Pure lag | `Routing(lag) Tr(2) Tn(6).xlsx` | `Routing(lag) Tr(3) Tn(2).xlsx` | `Routing(lag) Tr(3) Tn(4).xlsx` |
| Gamma (Nash cascade) | `Routing(gamma) Tr(2) Tn(6).xlsx` | `Routing(gamma) Tr(3) Tn(2).xlsx` | `Routing(gamma) Tr(3) Tn(4).xlsx` |
| Lag-then-smooth | `Routing(lag_then_smooth) Tr(2) Tn(6).xlsx` | `Routing(lag_then_smooth) Tr(3) Tn(2).xlsx` | `Routing(lag_then_smooth) Tr(3) Tn(4).xlsx` |

### Optimal-placement maps

| File | Description |
|------|-------------|
| `dominant_region_maps.xlsx` | Optimal-placement maps on a $200 \times 200$ log-spaced $(T_r, T_n)$ grid for nine Beta combinations ($\text{mode} \in \{0.1, 0.5, 0.9\} \times \kappa \in \{3, 10, 30\}$). Each combination has winner, temporal-intensity, and regret-based maps. Includes grid coordinates, config, and case parameter sheets. |

## Requirements

- Python 3.11+
- NumPy, SciPy, pandas, matplotlib, openpyxl

## License

See the accompanying paper for terms of use. The observed rainfall data are publicly available from the Korea Meteorological Administration (KMA).
