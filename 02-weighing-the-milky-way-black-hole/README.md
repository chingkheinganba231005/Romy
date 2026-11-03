# Chapter 2 — Weighing the Black Hole at the Center of the Milky Way

An end-to-end Machine Learning project in the style of Chapter 2 of *Hands-On Machine Learning with Scikit-Learn and TensorFlow*:
measure the mass of **Sagittarius A\*** and the distance to the Galactic Center from **25 years of real telescope data** of the stars orbiting it.

| File | What it is |
|---|---|
| `index.html` | The guide (open it in a browser): astronomy and ML theory, all the code with its real outputs, all the figures. |
| `sgr_a_star_mass_project.ipynb` | The complete notebook. Every number and figure of the guide comes from it. |
| `animations/sgr_a_star_animation.html` | Classroom animation driven by the exact model and fitted parameters (S2 on the sky with its radial-velocity curve, 3D orbit, the S-star cluster, and a "weigh it yourself" χ² game on the real data). |
| `datasets/sstars/` | Cached copy of the data table, so the notebook also runs offline. |
| `images/` | Figures saved by the notebook. |

## What you will do

1. Download the S-star table from CDS VizieR (with mirror fallback) and reshape it into tidy form.
2. Build a test set with **stratified sampling** on the distance to Sgr A\* (the rare close-approach points matter most).
3. Measure accelerations with local polynomial regression: they all point at one invisible spot and fall off like **1/r²** (with projection effects).
4. Write a Scikit-Learn **transformer** that stacks positions and velocities, and a **Kepler-orbit estimator** with 13 parameters.
5. Compare it with polynomial baselines using cross-validation and a 5-year **forecast** test.
6. Tune systematic error floors with `GridSearchCV`; estimate uncertainties with the **bootstrap** and see the mass–distance degeneracy.
7. Result: **M ≈ 4.5 million solar masses, R0 ≈ 8.5 kpc** from S2 alone; independent orbits of seven other S-stars follow Kepler's third law with the same mass.
8. "Launch": predict S2's 2018 pericentre passage (observed by GRAVITY in 2018) and the general-relativity effects that make the Newtonian model drift.

## Data (real)

S. Gillessen et al. (2017), *An Update on Monitoring Stellar Orbits in the Galactic Center*, ApJ 837, 30 — Table 5 (VizieR catalog J/ApJ/837/30): astrometry 1992–2016 and radial velocities 2000–2016 from ESO NTT/VLT, Keck and Gemini.

## Run it

```bash
python3 -m pip install -U jupyter numpy pandas matplotlib scipy scikit-learn
jupyter notebook sgr_a_star_mass_project.ipynb
```

The full notebook takes about 10 minutes (the grid search, the bootstrap and the multi-star fits refit the orbit many times).
