# How Does Spectral Resolution Influence Net Doppler Shifts?

This repository documents my research and development since the summer of 2025. The primary goal of this project is to determine how an instrument's spectral resolution affects our measurement of horizontal wind speeds in exoplanet atmospheres. By studying net Doppler shifts, I am evaluating how data quality influences the physical parameters we derive.

The project is divided into two distinct parts:

## The Ideal Case
This phase utilizes an "Ideal" dataset to establish a baseline for the atmospheric signal. In this scenario, we do not account for external noise or environmental factors that typically complicate observations. This allows for a pure look at the atmospheric physics by ignoring variables such as:

* **Telluric Absorptions:** The signal interference caused by Earth's atmosphere.
* **System Dynamics:** The specific motion of the planet, including its orbit and proper motion.
* **Instrument Efficiency:** The signal-to-noise ratio (SNR) constraints typical of physical hardware.

## The Real Case
This phase moves toward realistic observational conditions using the **[scope](https://scope-astr.readthedocs.io/en/latest/)** package, maintained by Arjun Savel at the University of Maryland, College Park. 

The **scope** package is used to simulate ground-based, High-Resolution Cross-Correlation Spectroscopy (HRCCS) of exoplanet atmospheres. This dataset incorporates the various complexities found in real-world observations.

By comparing these two cases, this project aims to quantify the impact of spectral resolution on our ability to map the climates of worlds beyond our solar system accurately.

**Quick Start**
