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
