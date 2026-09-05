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

Within each object folder, files are organized by **observation geometry**: emission or transmission.

An emission spectrum comes from the planet's dayside. The planet's own atmosphere emits light, and we observe it during secondary eclipse. A transmission spectrum, on the other hand, is detected during transit, when the planet passes in front of the star and blocks its light, so we cannot see the planet directly. However, some starlight passes through the atmosphere at the terminator, the boundary between the planet's day side and night side. Molecules in the atmosphere absorb this light at specific wavelengths, producing an absorption spectrum.

The table below summarizes the difference:

| | Emission | Transmission |
|---|---|---|
| **When observed** | Secondary eclipse (planet passes behind the star) | Transit (planet passes in front of the star) |
| **What we see** | Light emitted from the planet's dayside | Starlight filtered through the planet's atmosphere at the terminator |
| **How it works** | The planet's own atmosphere emits light, producing the emission spectrum | The planet blocks direct starlight, but some light passes through the atmosphere at the terminator, where molecules absorb specific wavelengths, producing an absorption spectrum |

Files are further subdivided by physical model:

* **Magnetic Models**: non-magnetic (`0G`) vs. magnetic (`3G`) configurations
* **Wind Profiles**: static atmospheres (`Spec_0`) vs. active wind speeds (`Spec_1`)
* **Chemical Species**: CO (infrared, IR) vs. H₂O (visible, VIS)

---

## File Naming Convention

Files follow a consistent pattern combining the categories above, but the exact format differs between planets. Here's how to read each one.

**WASP-121b:**

```
Spec_0_asp-121b-0G_IR_phase_0.0_inc_00.00.0000.00.dat
```

This reads as: **wind profile** (`Spec_0`), **planet** (WASP-121b), **magnetic model** (`0G`, non-magnetic), **chemical species** (`IR`, meaning CO), **orbital phase** (`phase_0.0`), and **inclination** (`inc_00.00.0000.00`).

**WASP-76b:**

```
Wasp76b-0G-Fefull_0.dat
```

This reads as: **planet** (WASP-76b), **magnetic model** (`0G`, non-magnetic), **chemical species and Doppler setting** (`Fefull_0`).

The trailing number distinguishes the Doppler setting: `_0` for Doppler off, `_1` for Doppler on.

---

## Contact

**Sarunyapat (Pat) Phoompuang**
Master's Student, Imperial College London
[sphoom22@terpmail.umd.edu](mailto:sphoom22@terpmail.umd.edu)

**Research Advisor:** Dr. Hayley Beltz, Postdoctoral Associate, University of Kansas
[hbeltz@ku.edu](mailto:hbeltz@ku.edu)
