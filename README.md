# DJF precipitation over North Kalimantan: Promax-rotated PCA of ERA5, 1955–2025

Derived outputs and analysis scripts for the manuscript *Leading Modes and a Candidate Decadal Shift in
December–February Precipitation over North Kalimantan, Indonesia: A Promax-Rotated Principal Component
Analysis of ERA5, 1955–2025* (A. Mahardika and A. Mulsandi, STMKG).

Archived version (DOI): https://doi.org/10.5281/zenodo.[isi setelah rilis]

## Contents

| File | Description |
|---|---|
| `pc_scores_promax_v2.csv` | Promax (κ = 3) PC1–PC4 scores per DJF season; `Year` = January year (1956 = DJF 1955/56) |
| `loadings_promax_v2.csv` | Promax pattern loadings on the 15 × 15 grid (1.0–4.5°N, 114.5–118.0°E) |
| `Komposit_tahun_PC1_PC4.csv` | Seasons in each composite phase (scores ≥ +0.5 and ≤ −0.5); Supplementary Table S1 |
| `Tabel2_tau.csv`, `tabel3.csv` | [isi: jelaskan, dan sebutkan tabel naskah yang sesuai (Table 2/3/4)] |
| `scripts/` | Analysis and figure scripts (see below) |
| `requirements.txt` | Python package versions |

## Scripts

- `aji_fig1b.py`: Figure 1b (needs `validasi_era5_bmkg_fig2.py` in the same folder)
- `aji_fig6v3.py`: Figure 6, SST correlation maps (FDR and effective sample size)
- [isi: skrip PCA/Promax, uji sensitivitas, Kendall, komposit, Pettitt/TFPW/bootstrap, validasi ERA5–BMKG]

## Input data (not redistributed)

ERA5 monthly averaged data from the Copernicus Climate Data Store:
single levels https://doi.org/10.24381/cds.f17050d7, pressure levels https://doi.org/10.24381/cds.6860a573
(Hersbach et al., 2020). Retrieval dates are given in the manuscript (Data availability).
Boundaries: GADM 4.1. Climate indices (Niño 3.4, DMI, PDO, WPI): sources in Section 2.5 of the manuscript.
The BMKG ZOM9120 seasonal-zone series were provided by A. Mulsandi and are available from the authors on reasonable request.

## Licence

Code: MIT. Derived data and tables: CC BY 4.0.
