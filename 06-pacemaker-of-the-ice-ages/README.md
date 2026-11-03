# Chapter 6 — The Pacemaker of the Ice Ages

An end-to-end Machine Learning project in the style of Chapter 2 of *Hands-On Machine Learning with Scikit-Learn and TensorFlow*:
rediscover the **Milankovitch cycles** that pace the ice ages, from **800,000 years of Antarctic ice-core data** and the astronomical solution for the Earth's orbit, and build a model that turns orbits into ice ages.

| File | What it is |
|---|---|
| `index.html` | The guide: paleoclimate and ML theory, all the code with its real outputs, all the figures. |
| `ice_ages_project.ipynb` | The complete notebook (about a minute). |
| `animations/ice_ages_animation.html` | Classroom animation: the Earth's orbit and 65°N sunshine at any epoch, and a time machine from 800,000 years ago to 100,000 years ahead (forcing, model state, ice cap, real temperature). |
| `datasets/` | Cached EPICA, CO₂, LR04 and La2004 files. |

## What you will do

1. Load EPICA Dome C temperature, the Antarctic CO₂ composite, the LR04 benthic stack and the La2004 orbital solution.
2. Resample the unevenly spaced ice core and hold out the last glacial cycle as a **time-series test set**.
3. Find the orbital periods (41, ~100 and 23 kyr) with a Lomb–Scargle periodogram — Hays, Imbrie & Shackleton (1976).
4. Engineer the physics feature: **65°N summer insolation** from eccentricity, obliquity and precession; add **lag features**.
5. Compare a linear model and gradient boosting (which overfits) with **blocked cross-validation**.
6. Tune a non-differentiable three-state **ice-sheet model** (after Paillard 1998) with `RandomizedSearchCV`: it reproduces the timing of the glacial terminations of the last 800,000 years.
7. Evaluate honestly on the last glacial cycle, in RMSE and in the frequency domain.
8. Forecast the next ice age from the orbit, then monitor two drifts: the **Mid-Pleistocene Transition** (41 kyr → 100 kyr world) and today's **CO₂** far outside the training range.

## Data (real)

EPICA Dome C (Jouzel et al. 2007), Antarctic CO₂ composite (Bereiter et al. 2015), LR04 (Lisiecki & Raymo 2005) — NOAA World Data Service for Paleoclimatology; La2004 orbital solution (Laskar et al. 2004) — IMCCE.

## Run it

```bash
python3 -m pip install -U jupyter numpy pandas matplotlib scipy scikit-learn
jupyter notebook ice_ages_project.ipynb
```
