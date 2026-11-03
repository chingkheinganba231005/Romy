# Chapter 4 — Discovering Dark Energy: The Accelerating Universe

An end-to-end Machine Learning project in the style of Chapter 2 of *Hands-On Machine Learning with Scikit-Learn and TensorFlow*:
discover the **accelerating expansion of the Universe** (Nobel Prize 2011) and measure the **Hubble constant** from 1,701 real Type Ia supernova light curves.

| File | What it is |
|---|---|
| `index.html` | The guide: cosmology and ML theory, all the code with its real outputs, all the figures. |
| `dark_energy_project.ipynb` | The complete notebook (runs in under a minute). |
| `animations/dark_energy_animation.html` | Classroom animation: tune Ωm, ΩΛ, H0 against the binned real data, explore the map of universes, watch the expansion history. |
| `datasets/pantheon_plus/` | Cached Pantheon+ table and compressed covariance matrix. |

## What you will do

1. Load Pantheon+ and split it with `StratifiedGroupKFold` (same supernova, several surveys → group leakage).
2. Rediscover Hubble's law with a one-parameter regression.
3. Build a standard candle: a two-feature linear regression on light-curve stretch and colour (Tripp/Phillips relations) halves the scatter.
4. Write a cosmology estimator that learns the supernova luminosity and H0 through the **distance ladder** (Cepheid calibrators + Hubble flow).
5. Compare five universes with Δχ², `GroupKFold` cross-validation and a k-NN baseline; measure q0 < 0 with a model-agnostic Taylor expansion.
6. Grid-scan the Ωm–ΩΛ plane, refit with the full covariance (generalized least squares), group-bootstrap the errors.
7. Result: **H0 ≈ 73.7 km/s/Mpc, Ωm ≈ 0.32, ΩΛ ≈ 0.68, q0 ≈ −0.5** — matter-only universe excluded by Δχ² ≈ 550.
8. Monitor: the **Hubble tension** with Planck, and evolving dark energy (w0–wa).

## Data (real)

Pantheon+ (Scolnic et al. 2022; Brout et al. 2022) with SH0ES Cepheid calibrators (Riess et al. 2022), from the public data release at github.com/PantheonPlusSH0ES/DataRelease.

## Run it

```bash
python3 -m pip install -U jupyter numpy pandas matplotlib scipy scikit-learn
jupyter notebook dark_energy_project.ipynb
```
