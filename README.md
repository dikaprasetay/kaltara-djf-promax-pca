# DJF precipitation over North Kalimantan: Promax-rotated PCA of ERA5, 1955–2025

Derived outputs and analysis scripts for the manuscript *Leading Modes and a Candidate Decadal Shift in
December–February Precipitation over North Kalimantan, Indonesia: A Promax-Rotated Principal Component
Analysis of ERA5, 1955–2025* (A. Mahardika and A. Mulsandi, STMKG).

Archived version (DOI): https://doi.org/10.5281/zenodo.23437193

## Contents

### Derived data and tables

| File | Description |
|---|---|
| `pc_scores_promax_v2.csv` | Promax (κ = 3) PC1–PC4 scores per DJF season; `Year` = January year (1956 = DJF 1955/56) |
| `loadings_promax_v2.csv` | Promax pattern loadings on the 15 × 15 grid (1.0–4.5°N, 114.5–118.0°E) |
| `factor_correlation.csv` | Correlation matrix of the Promax factors (Table 2) |
| `pc_scores_varimax.csv` | Varimax PC scores, used for the Varimax comparison |
| `sens_north.csv` | Eigenvalues, explained variance and North's rule errors (Table 1, unrotated row) |
| `sens_varians_total.csv` | Sums of the Promax pattern and structure variance shares (Table 1) |
| `sens_k.csv`, `sens_kappa.csv`, `sens_varimax.csv` | Tucker congruence of the Promax loadings for other numbers of components k, other κ and Varimax (Table 3) |
| `aji_tabel1.csv` | Table 1 as formatted for the manuscript (variance shares of PC1–PC4) |
| `aji_tabel3.csv` | Table 3 as formatted for the manuscript (Tucker congruence) |
| `Tabel2_tau.csv` | Kendall τb between PC1–PC4 scores and the climate indices DMI, Niño 3.4, PDO and WPI (Table 4; q-values are given in the manuscript) |
| `validasi_mask_sensitivitas.csv` | ERA5 versus BMKG ZOM9120 validation statistics for the full domain, the provincial mask and the ZOM mask (Section 3.1) |
| `zom_kaltara_tabel.csv` | The seven North Kalimantan ZOM polygons: approximate area, centre and number of ERA5 cell centres inside each |
| `Komposit_tahun_PC1_PC4.csv` | Seasons in each composite phase (scores ≥ +0.5 and ≤ −0.5); Supplementary Table S1 |

### Scripts

The scripts are in `scripts/`. They were run in the order below. File paths inside the scripts point to
the authors' local folders and must be adapted. The header of each script documents its arguments.

| Step | Script | Output |
|---|---|---|
| 1 | `analisis_pca_promax_70musim.py` | PCA with Promax rotation (κ = 3): scores, loadings and factor correlations (Table 2) |
| 2 | `sensitivitas_pca.py` | Variance shares (Table 1) and sensitivity of the solution to the number of components, κ and Varimax (Table 3); writes `sens_*.csv` |
| 3 | `tabel2_korelasi_v2.py` | Kendall τb between PC scores and climate indices (Table 4) |
| 4 | `validasi_era5_bmkg_fig2.py` | ERA5 versus BMKG ZOM9120 validation (Figure 2) |
| 4b | `aji_validasi_mask.py` | ERA5–BMKG validation repeated with the cells inside the provincial boundary (GADM) and inside the ZOM polygons (needs `validasi_era5_bmkg_fig2.py` in the same folder); writes `validasi_mask_sensitivitas.csv` and `zom_kaltara_tabel.csv` |
| 5 | `aji_fig1a_v2.py`, `aji_fig1b.py` | Figure 1a, 1b (`aji_fig1b.py` needs `validasi_era5_bmkg_fig2.py` in the same folder) |
| 6 | `aji_fig3_v3.py` | Figure 3, pattern loadings |
| 7 | `fig_komposit_v2.py` | Figure 4, rainfall composites, and the composite-year list (Supplementary Table S1) |
| 8 | `fig_korelasi_v2.py` | Figure 5, correlation maps with local precipitation |
| 9 | `aji_fig6v3.py` | Figure 6, SST correlation maps (FDR and effective sample size) |
| 10 | `fig_sirkulasi_v2.py` | Figure 7, circulation composites |
| 11 | `aji_fig8_v3.py` | Figure 8, CAPE and vertical-motion composites |
| 12 | `aji_fig9_v3.py` | Figure 9, PC scores with Sen slope and Pettitt test |
| 13 | `aji_fig10_v3.py` | Figure 10, Sen slope of monthly precipitation |
| 14 | `aji_fig11_v3.py` | Figure 11, SST trend, Sulawesi Sea series and association with the PCs |
| – | `gaya_gambar.py` | Shared plotting style (imported by several figure scripts) |

Example (Figure 4):

```
py fig_komposit_v2.py --nc avgad.nc --scores hasil_pca/pc_scores_promax_v2.csv --shp gadm41_IDN_shp/gadm41_IDN_2.shp --out Fig_komposit_v2
```

## Input data (not redistributed)

ERA5 monthly averaged data from the Copernicus Climate Data Store:
single levels https://doi.org/10.24381/cds.f17050d7, pressure levels https://doi.org/10.24381/cds.6860a573
(Hersbach et al., 2020). Retrieval dates are given in the manuscript (Data availability).
Boundaries: GADM 4.1. Climate indices (Niño 3.4, DMI, PDO, WPI): sources in Section 2.5 of the manuscript.
The BMKG ZOM9120 seasonal-zone series were provided by A. Mulsandi and are available from the authors on reasonable request.

## Software

Python packages and versions are in `requirements.txt`.

## Licence

Code: MIT. Derived data and tables: CC BY 4.0.
