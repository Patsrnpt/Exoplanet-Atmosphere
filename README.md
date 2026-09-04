# How Does Spectral Resolution Influence Net Doppler Shifts?

*Mapping wind speeds in exoplanet atmospheres and how the instruments we use shape what we're able to see.*

*Specifically: finding the relationship between wind speed, spectral resolution, orbital phase, and magnetic field model.*

![Status](https://img.shields.io/badge/status-active-brightgreen)
![Python](https://img.shields.io/badge/python-3.x-blue)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## About This Project

Hi, I'm **Sarunyapat (Pat) Phoompuang**. I am a Master's student in Physics at **Imperial College London**. This repository documents research I began in the summer of 2025 at the **University of Maryland, College Park**, conducted under the guidance of **Dr. Hayley Beltz**, a postdoctoral associate at the **University of Kansas**.

The core question I'm chasing: *when we measure wind speeds on exoplanets by tracking Doppler shifts, how much does the resolution of our instrument distort what we see?* Real telescopes are noisy, imperfect, and limited, so before we trust what they tell us about alien weather, we need to know how much of the signal is real atmosphere and how much is instrumental artifact.

If you're curious about the project, want to dig into the data, or want to chat about exoplanet atmospheres, feel free to reach out. My contact info is at the bottom.

---

## Why This Matters

There's a tradeoff between ground-based and space-based telescopes. Ground-based telescopes can achieve higher spectral resolution and are cheaper to build at large apertures, but their observations pass through Earth's atmosphere first, introducing telluric absorption and other noise that has to be corrected for. Space-based telescopes avoid that atmospheric interference, giving cleaner data, but they operate at lower spectral resolution and come with higher cost and stricter size constraints.

This project's comparison between the Ideal and Real cases is a way of probing that tradeoff: how much resolution can you sacrifice, or gain, before it changes the wind speeds we derive?

---

## Table of Contents
- [The Two Phases of This Project](#the-two-phases-of-this-project)
  - [Phase 1: The Ideal Data](#phase-1-the-ideal-data)
  - [Phase 2: The Real Data](#phase-2-the-real-sata)
- [Data Structure](#data-structure)
- [File Naming Convention](#file-naming-convention)
- [Quick Start](#quick-start)
- [Contact](#contact)

---

## The Two Phases of This Project

Building or accessing instruments across a full range of spectral resolutions isn't feasible right now, so this project relies on modeling the atmosphere directly. Instead of observing the same planet at many different resolutions, we simulate what those observations would look like, and study how the resolution changes what we recover.

### Phase 1: The Ideal Data

This phase uses an **"Ideal" dataset** to establish a clean baseline for the atmospheric signal, with no external noise or environmental complications. It's a pure look at the underlying atmospheric physics.

### Phase 2: The Real Data

This phase moves toward realistic observing conditions using **[scope](https://scope-astr.readthedocs.io/en/latest/)**, a package maintained by Arjun Savel at the University of Maryland, College Park. For further information, see [Savel et al. 2024](https://arxiv.org/abs/2411.07303).

**scope** simulates ground-based, **High-Resolution Cross-Correlation Spectroscopy (HRCCS)** of exoplanet atmospheres, reintroducing the complexity that Phase 1 leaves out, so the dataset reflects what a real telescope would record. The simulation includes:

* **Telluric Absorptions**: signal interference caused by Earth's own atmosphere
* **System Dynamics**: the planet's motion, including orbit and proper motion
* **Instrument Efficiency**: the signal-to-noise ratio (SNR) limits of real hardware
* **Blaze Function**: the wavelength-dependent throughput of the spectrograph's grating, which shapes the continuum of the observed spectrum

> Comparing the Ideal and Real cases quantifies how spectral resolution affects our ability to map the climates of worlds beyond our solar system.

---

## Data Structure

There are two primary data folders in this repository:

| Folder | Purpose |
|---|---|
| **[Ideal Data](https://github.com/Patsrnpt/Exoplanet-Atmosphere/tree/main/Ideal%20Data)** | Baseline simulations, no noise. Covers **WASP-76b** (multiple magnetic models) and **WASP-121b** (primary object of study). |
| **[Scope Data](https://github.com/Patsrnpt/Exoplanet-Atmosphere/tree/main/Scope%20Data)** | Input data prepared to match the spectral resolution expected by the **scope** package. Like the Ideal Data, it doesn't yet include any realistic observational effects. This is the dataset that gets passed through **scope** to produce the simulated spectra. |

Within each object folder, files are organized by **observation geometry**:

* **Emission**: light emitted from the planet's own atmosphere, observed during secondary eclipse
* **Transmission**: stellar light filtered through the planet's atmosphere, observed during transit

...and further subdivided by physical model:

* **Magnetic Models**: non-magnetic (`0G`) vs. magnetic (`3G`) configurations
* **Wind Profiles**: static atmospheres (`Spec_0`) vs. active wind speeds (`Spec_1`)
* **Chemical Species**: CO (infrared, IR) vs. H₂O (visible, VIS)

---

## File Naming Convention

Files follow a consistent pattern combining the categories above. For example:

```
WASP121b_Transmission_0G_Spec1_CO.fits
```

This reads as: **WASP-121b**, **transmission** geometry, **non-magnetic** model, **active wind** profile, **CO** species.

---

## Quick Start

```bash
# clone the repository
git clone https://github.com/Patsrnpt/Exoplanet-Atmosphere.git
cd Exoplanet-Atmosphere

# (recommended) set up a virtual environment
python -m venv venv
source venv/bin/activate  # on Windows: venv\Scripts\activate

# install dependencies
pip install -r requirements.txt
```

Once you've identified the appropriate data folder for your analysis (see [Data Structure](#data-structure) above), you're ready to run the analysis scripts provided in this repository.

---

## Contact

I'd love to hear from you, whether you have questions or spot something worth fixing.

**Sarunyapat (Pat) Phoompuang**
Master's Student, Physics, Imperial College London
[sphoom22@terpmail.umd.edu](mailto:sphoom22@terpmail.umd.edu)

**Research Advisor:** Dr. Hayley Beltz, Postdoctoral Associate, University of Kansas
