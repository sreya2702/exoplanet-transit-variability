# Exoplanet Transit Detection under Stellar Variability

This repository contains two TESS light curve analysis projects exploring how stellar variability affects exoplanet transit detection.

## Project 1: WASP-18 (Controlled Case)

A known transiting exoplanet was used as a baseline. Synthetic stellar variability was injected into the light curve to test how increasing variability affects transit detection using Box Least Squares (BLS).

### Result
As variability increases, the transit signal becomes distorted and period recovery degrades.

## Project 2: AU Mic (Real Active Star)

A highly active star was analysed using TESS data. Strong stellar rotation and flare activity dominate the light curve.

### Result
Standard BLS fails to recover a reliable planetary period due to stellar variability and flare contamination.

## Tools Used
- Python
- Lightkurve
- NumPy
- Matplotlib
- TESS data

## Motivation
This project demonstrates the challenges of exoplanet detection in active stellar environments, relevant to modern surveys such as SPECULOOS.
