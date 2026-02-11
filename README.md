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

## Quick Start
Before you begin, there are two primary data structures within this repository that you should be familiar with:

### 1. [Ideal Data](https://github.com/Patsrnpt/Exoplanet-Atmosphere/tree/main/Ideal%20Data)
This folder contains the baseline simulations. It focuses on two specific planets: **WASP-76b** and **WASP-121b**. While WASP-76b includes multiple magnetic models, WASP-121b serves as the primary object of study for this research.

### 2. [Scope Data](https://github.com/Patsrnpt/Exoplanet-Atmosphere/tree/main/Scope%20Data)
This folder is utilized after the ideal data analysis is complete. This dataset is integrated with the **scope** package to account for the observational and environmental factors mentioned above.

### Data Classification and File Naming
Within each object folder, files are organized by observation geometry and physical parameters:

* **Emission:** Data representing the light emitted from the planet's own atmosphere, typically observed during secondary eclipse.
* **Transmission:** Data representing the stellar light filtered through the planet's atmosphere, observed as the planet passes in front of the host star.

The spectral data is subdivided based on the following physical models:
* **Magnetic Models:** Includes non-magnetic (0G) and magnetic (3G) configurations.
* **Wind Profiles:** Differentiated between static atmospheres (Spec_0) and those with active wind speeds (Spec_1).
* **Chemical Species:** Separated by detectable ranges, specifically CO (IR: Infrared) and H2O (VIS: Visible).

Once you have identified the appropriate data folder for your analysis, you are ready to use the scripts provided in this repository.

---

If you have any questions or would like to collaborate, feel free to contact me at: [sphoom22@terpmail.umd.edu](mailto:sphoom22@terpmail.umd.edu).
