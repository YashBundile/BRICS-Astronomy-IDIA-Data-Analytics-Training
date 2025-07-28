# Identification and Characterization of Rare Stellar Populations in ESA Gaia DR3 Using Machine Learning

This repository contains my capstone project developed as part of the **BRICS Astronomy and IDIA Data Analytics Training Programme**. The objective of this study is to use **unsupervised machine learning techniques** to identify **rare stellar populations** in the **ESA Gaia Data Release 3 (DR3)**.

## Objective

To identify and characterize rare stellar types by applying **dimensionality reduction (UMAP)** and **anomaly detection (Isolation Forest)** to a high-quality subset of Gaia DR3 data. Outliers in the multidimensional feature space are flagged as candidates for **unusual or unclassified stellar populations**.

---

## Dataset: ESA Gaia DR3

We used a filtered sample of **10,000 stars** from Gaia DR3 that met the following high-quality criteria:

- `parallax > 2 mas` → stars within ~500 pc
- `phot_g_mean_mag < 18` → ensures photometric precision
- `parallax_over_error > 10` → high-confidence distance
- `bp_rp IS NOT NULL` → valid color index
- `ruwe < 1.4` and low `astrometric_excess_noise` → reliable astrometry

These criteria ensure robust astrometric and photometric measurements.

---

## Features Used

- **Astrometry**: `ra`, `dec`, `parallax`, `pmra`, `pmdec`, `radial_velocity`
- **Photometry**: `phot_g_mean_mag`, `bp_rp`
- **Derived**: `abs_mag_g` (absolute magnitude), `v_tan` (tangential velocity)

These features provide a comprehensive view of stellar position, motion, and color—ideal for anomaly detection.

---

## Methods

### 1. Data Acquisition  
Queried Gaia DR3 using `Astroquery`.

### 2. Preprocessing & Feature Engineering  
Derived key features like **absolute G magnitude**, **tangential velocity**, and filtered out unreliable sources.

### 3. Visualization  
- **Color-Magnitude Diagram (CMD)** to visualize stellar evolutionary phases  
- **Correlation heatmap** of derived features  
- **Histograms** to analyze feature distributions

### 4. Dimensionality Reduction  
- **UMAP** (Uniform Manifold Approximation and Projection) for nonlinear projection into 2D

### 5. Clustering & Anomaly Detection  
- **DBSCAN** for unsupervised clustering  
- **Isolation Forest** to flag anomalies (rare stars)

### 6. Validation  
- Cross-matched rare stars with the **SIMBAD** catalog to check for known identifiers

---

## Results

- Outliers identified using Isolation Forest occupy **sparse regions** in UMAP space, suggesting unusual astrophysical properties.
- SIMBAD cross-matching confirmed some as known rare types like **white dwarfs**, **subdwarfs**, or **high-velocity stars**.
- Visualizations (CMD and UMAP) clearly separate these stars from the dominant population.

---

## Technologies Used

- **Python**, **Google Colab**
- `Astroquery`, `Astropy`, `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`
- `Scikit-learn`, `UMAP-learn`
- `IsolationForest`, `DBSCAN`

---

## Future Work

- Apply the pipeline to **larger Gaia DR3 subsets**
- Incorporate **variability** and **spectroscopic data**
- Search for **metal-poor halo stars**, **hypervelocity stars**, and **exotic binaries**
- Perform deeper **cross-matching** with SIMBAD, Vizier, and other catalogs

---

## References

- Gaia Collaboration et al. (2023), *Gaia DR3: Summary*, A&A, [DOI:10.1051/0004-6361/202243940](https://doi.org/10.1051/0004-6361/202243940)
- McInnes et al. (2018), *UMAP*, [arXiv:1802.03426](https://arxiv.org/abs/1802.03426)
- Liu et al. (2008), *Isolation Forest*, [DOI:10.1109/ICDM.2008.17](https://doi.org/10.1109/ICDM.2008.17)

---

## Acknowledgements

This project was conducted under the **BRICS Astronomy & IDIA Training Programme**, with guidance from mentors and scientists across BRICS nations. Special thanks to the organizers for the opportunity to explore cutting-edge research in data-intensive astronomy.
