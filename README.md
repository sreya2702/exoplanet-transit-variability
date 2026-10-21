# Exoplanet transit detection under stellar variability

A small, reproducible **Python / TESS / Lightkurve research case study** investigating why transit searches become difficult when photometric variability contaminates a light curve. This project uses **Box Least Squares (BLS)**, not a machine-learning classifier, and does **not** claim discovery of a new exoplanet.

## Analyses included

**WASP-18 — controlled sensitivity test.** Download and preprocess a TESS light curve, estimate the strongest BLS period, then inject 2.5-day sinusoidal variability at increasing amplitudes. Compare the recovered BLS peak with the baseline and visualise the effect.

The original executed notebook recorded:

| Test | Strongest BLS peak (days) |
| --- | ---: |
| WASP-18 baseline | 0.94123489 |
| Injected amplitude 0.003 | 0.94123489 |
| Injected amplitude 0.010 | 2.50797158 |

These values are **saved outputs from the original notebook**, not a guarantee of identical results with newer archive products or software versions. The strong perturbation caused BLS to favour a peak close to the injected variability period rather than the transit baseline. This is a limited, controlled demonstration, not a measured false-positive rate.

**AU Mic — active-star challenge.** Apply the same simple BLS preprocessing to a TESS light curve from an active star. The original notebook returned a strongest BLS peak at **0.33539919 days**. That peak **is not a validated planetary orbital period**, and the experiment is not evidence of an absence of planets.

## Repository contents

- [`exoplanet_transit_analysis.ipynb`](exoplanet_transit_analysis.ipynb) — **clean, structured notebook** with explanation, plots and runtime-derived results. Use this for review or reproduction.
- [`exoplanet_1.ipynb`](exoplanet_1.ipynb) — original exploratory notebook with saved code outputs and plots, preserved unchanged for transparency.
- [`requirements.txt`](requirements.txt) — Python dependencies.

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\\Scripts\\activate
python -m pip install -r requirements.txt
jupyter notebook
```

Open `exoplanet_transit_analysis.ipynb` and choose **Run All**. Downloading TESS data requires an internet connection. The notebook prints the selected TESS product/sector; it chooses the first returned product to approximate the original exploratory workflow.

## Scientific caveats

- Only one automatically selected TESS product per star is analysed; product order may change.
- Variability is deliberately injected *after* flattening. It is a simple sinusoid, not a realistic stellar surface model.
- Strongest BLS peak is not proof of a transit. The project does not estimate false-alarm probabilities, completeness, or astrophysical parameters.
- Future work: multiple sectors, realistic stellar variability and flare modelling, injection-recovery ensembles, period validation and more robust detrending.

**Project focus:** observational time series, numerical experimentation, signal processing, and careful interpretation of algorithmic limitations.
