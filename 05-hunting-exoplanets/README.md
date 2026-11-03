# Chapter 5 — Hunting Exoplanets in NASA Kepler Data

An end-to-end Machine Learning project in the style of Chapter 2 of *Hands-On Machine Learning with Scikit-Learn and TensorFlow*:
find the planets of **Kepler-90** in its raw Kepler light curve, and build a classifier that tells **real planets from false positives** using the full Kepler catalog.

| File | What it is |
|---|---|
| `index.html` | The guide: transit astronomy and ML theory, all the code with its real outputs, all the figures. |
| `exoplanet_project.ipynb` | The complete notebook (about 3 minutes). |
| `animations/exoplanet_animation.html` | Classroom animation: anatomy of a limb-darkened transit, the Kepler-90 system with its predicted light curve, and interactive phase-folding of the real data. |
| `datasets/` | Cached Kepler-90 light curve (CSV) and the NASA KOI table. |

## What you will do

1. Download 4 years of Kepler-90 photometry from NASA's MAST archive and the 9,564-row KOI table from the NASA Exoplanet Archive.
2. Split by star (`StratifiedGroupKFold`), holding Kepler-90 out entirely for the final end-to-end test.
3. Engineer a physics feature: observed / expected transit duration from Kepler's third law.
4. Spot **target leakage** (the catalog's vetting flags give a "99.4%" model).
5. Compare logistic regression, random forest and gradient boosting in a full `Pipeline` + `ColumnTransformer`; tune with `RandomizedSearchCV`; read permutation importances; choose a threshold from precision/recall.
6. Detrend the light curve with a custom transformer and run an iterative **Box Least Squares** transit search.
7. Result: **7 of Kepler-90's 8 known planets recovered** from raw data and all vetted as planets (test ROC AUC 0.97); a quarter-edge artifact exposes an out-of-distribution failure, fixed with a guard rail.
8. Monitor: check training/serving skew, rank the 1,977 unconfirmed candidates, list small temperate worlds.

## Data (real)

Kepler long-cadence light curves (MAST, STScI); KOI cumulative table (NASA Exoplanet Archive, Caltech/IPAC).

## Run it

```bash
python3 -m pip install -U jupyter numpy pandas matplotlib scipy scikit-learn astropy astroquery
jupyter notebook exoplanet_project.ipynb
```
