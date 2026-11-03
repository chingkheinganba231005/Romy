# Chapter 3 — Rediscovering Neptune: Finding a Planet in the Residuals

An end-to-end Machine Learning project in the style of Chapter 2 of *Hands-On Machine Learning with Scikit-Learn and TensorFlow*:
explain the anomalous motion of Uranus, infer an unseen planet, and "point the telescope" on the night of **23 September 1846** — as Le Verrier did.

| File | What it is |
|---|---|
| `index.html` | The guide (open it in a browser): celestial mechanics and ML theory, all the code with its real outputs, all the figures. |
| `neptune_project.ipynb` | The complete notebook (runs in about 2 minutes). |
| `animations/neptune_animation.html` | Classroom animation driven by the simulated orbits and fitted parameters: the hidden pull and the residuals, an interactive grid-search map, and the eyepiece view of 1846. |
| `datasets/nasa/` | Cached NASA/JPL Horizons tables, so the notebook also runs offline. |
| `images/` | Figures saved by the notebook. |

## What you will do

1. Download Uranus's sky positions (1690–1846) and the positions of the Earth, Jupiter and Saturn from NASA/JPL Horizons.
2. Sample them like history: night-time observations after Herschel's 1781 discovery, a few pre-discovery positions before.
3. Test the Titius–Bode "law" with a linear regression on an attribute combination (it predicts ~37–39 AU).
4. Build a **gravity simulator** (Newton + numerical integration with SciPy) wrapped as a Scikit-Learn estimator, and fit Uranus's orbit.
5. Read the residuals (O − C): with Jupiter and Saturn, the error is still 12″ RMS with 2.4′ waves — Bouvard's problem.
6. Linearise the problem: a custom `PlanetXFeatures` transformer + `LinearRegression` in a `Pipeline`, and a **`GridSearchCV`** over the distance and longitude of an unknown planet.
7. Result: planet X at **30 AU, ~16 Earth masses**, residuals down to ~0.5″; on 1846-09-23 the prediction lies **~1.4° from Neptune**. The data overrule Bode's law.
8. Monitoring lessons: Vulcan and general relativity (model-class drift), Lowell's Planet X (fitting noise).

## Data

NASA/JPL Horizons (DE440/441). The historical telescope measurements of Uranus used by Le Verrier are not available in digitised form, so this chapter uses NASA's ephemeris, which is fitted to real observations and contains the true pull of Neptune. Neptune's own position is only downloaded at the end, to check the prediction.

## Run it

```bash
python3 -m pip install -U jupyter numpy pandas matplotlib scipy scikit-learn
jupyter notebook neptune_project.ipynb
```
