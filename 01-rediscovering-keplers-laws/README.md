# Chapter 1 — Rediscovering Kepler's Laws

An end-to-end Machine Learning project in the style of Chapter 2 of *Hands-On Machine Learning with Scikit-Learn and TensorFlow*:
rediscover Kepler's three laws of planetary motion from **Tycho Brahe's raw naked-eye observations of Mars (1582–1600)** and NASA data.

| File | What it is |
|---|---|
| `index.html` | The guide (open it in a browser). Book-style chapter: theory, code, outputs, figures. |
| `kepler_laws_project.ipynb` | The complete notebook. Every number and figure of the guide comes from it. |
| `animations/kepler_laws_animation.html` | Classroom animation driven by the exact equations and fitted parameters (4 tabs). |
| `datasets/` | Cached data, so the notebook also runs offline. |
| `images/` | Figures saved by the notebook. |

## What you will do

1. Load 940 declinations of Mars measured by Tycho Brahe (transcribed from the *Opera Omnia*).
2. Clean them: parse Latin timestamps, morning/evening markers, Julian vs Gregorian calendars.
3. Triangulate Mars's orbit from NASA/JPL Horizons directions (Kepler's 687-day trick) and fit a conic with `LinearRegression` → **ellipse, Sun at a focus (Law 1)**.
4. Combine attributes: ½ r² dθ/dt is constant → **equal areas (Law 2)**.
5. Write a Scikit-Learn estimator for four world-models (circle, equant, eccentric circle + areas, ellipse + areas), fit them to Tycho's raw data and select with `GroupKFold` cross-validation → the equant misses unseen apparitions by **8.3′ — Kepler's eight arcminutes**.
6. Fine-tune robust losses with `GridSearchCV`, analyse errors, evaluate on held-out apparitions, compare with NASA.
7. Regress log T on log a for the planets (NASA fact sheet) → **T² ∝ a³ (Law 3)**, and weigh Jupiter with its moons.
8. Monitor the 1600 model for four centuries against NASA (concept drift).

## Data (all real — no simulation)

* Tycho Brahe's Mars declinations — *Tychonis Brahe Dani Opera Omnia* (ed. Dreyer, vols. 10–13), transcribed by Wayne Pafko (2000), spreadsheet by Christophe Yamahata.
* NASA/JPL Horizons ephemerides (DE440/441) — geocentric positions of Mars and the Sun.
* NASA NSSDC Planetary Fact Sheet and Jovian Satellite Fact Sheet.

## Run it

```bash
python3 -m pip install -U jupyter numpy pandas matplotlib scipy scikit-learn openpyxl lxml
jupyter notebook kepler_laws_project.ipynb
```

The full notebook runs in about 7 minutes on a laptop (the cross-validation and grid search refit the orbit models many times).
