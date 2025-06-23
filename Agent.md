# Repo Overview

This repository contains the source code of the **enviPat** R package (v2.7) for isotope pattern and mass spectrometry envelope calculations.

## Structure
- `R/` – R functions implementing isotope pattern generation, envelope calculation, chemical formula utilities and other helpers.
- `src/` – C code providing optimized algorithms for isotope fine structure calculations accessed from R via `useDynLib`.
- `data/` – Example datasets (`isotopes`, `chemforms`, `adducts`, `resolution_list`) used in examples and unit operations.
- `man/` – R documentation (`.Rd` files) for the exported functions and data objects.
- `inst/` – Additional package files including a `CITATION` file.
- `DESCRIPTION`, `NAMESPACE`, `NEWS` – Standard R package metadata and change log.
- `README.md` – Basic usage and installation instructions.

## Key Functionality
- `isopattern()` computes isotopic fine structures for formulas using fast transition tree algorithms (with pruning thresholds, multiple algorithms available).
- `envelope()` convolves isotopic patterns into theoretical peak envelopes at a given instrument resolution.
- `check_chemform()`, `mergeform()`, `multiform()`, and helpers parse, combine and validate chemical formulas.
- `getR()` fits smoothing splines to experimental resolution data, enabling interpolation.
- Additional utilities (`isowrap()`, `vdetect()`, etc.) support batch processing and valley detection.

## Build/Testing
The package relies on compiled C code and is typically built and installed via standard R tooling (`R CMD build` / `R CMD INSTALL`). This repository does not include an automated test suite.

## R functions
- `check_chemform()`: validates and normalizes chemical formula strings. It can return corrected formulas together with monoisotopic masses or lists of element counts.
- `check_ded()`: checks whether a deduction formula is fully contained in a set of formulas and flags any insufficient atom counts.
- `check_several()`: examines several isotope patterns and reports overlapping m/z values within a user supplied tolerance.
- `envelope()`: converts stick isotope patterns into simulated peak profiles (Gaussian or Cauchy--Lorentz) at a specified instrument resolution.
- `.onAttach()`: prints the package welcome message when the library is loaded in R.
- `getR()`: fits a smoothing spline to experimental mass/resolution data and predicts resolution values for new masses.
- `isopattern()`: generates theoretical isotope patterns via compiled C algorithms, applying charge correction and intensity thresholding.
- `isowrap()`: convenience wrapper performing resolution interpolation, pattern generation, profile convolution and centroid or valley detection.
- `mergeform()`: adds two chemical formulas element-wise and returns the combined result.
- `multiform()`: multiplies the atom counts of a formula by a constant factor.
- `subform()`: subtracts one formula from another after verifying that all required atoms are present.
- `vdetect()`: detects centroids, intensoids or valley positions in profile data using compiled code.

