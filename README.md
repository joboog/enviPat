# enviPat

`enviPat` is an R package for calculating isotope patterns and theoretical mass spectrometry envelopes. It implements fast algorithms for isotope fine structure calculations and tools for subsequent envelope generation, centroidization, and adduct handling.

## Installation

The stable release is available on CRAN:

```r
install.packages("enviPat")
```

Development versions can be installed from GitHub using `devtools`:

```r
# install.packages("devtools")
devtools::install_github("blosloos/enviPat")
```

## Basic Example

The following code generates isotope patterns for several chemical formulas and then convolutes them into theoretical envelopes:

```r
library(enviPat)

# load data sets bundled with the package
data(isotopes)
data(chemforms)

# calculate isotope patterns for a subset of formulas
pattern <- isopattern(
  isotopes,
  chemforms[1:5],
  threshold = 0.1,
  plotit = TRUE,
  charge = FALSE,
  algo = 2
)

# convert the patterns to envelopes at 1 million resolving power
profiles <- envelope(
  pattern,
  ppm = FALSE,
  dmz = 0.0001,
  frac = 1/4,
  env = "Gaussian",
  resolution = 1e6,
  plotit = TRUE
)
```

## Citation

If you use `enviPat` in your work, please cite:

Loos, M.; Gerber, C.; Corona, F.; Hollender, J.; Singer, H. (2015). Accelerated isotope fine structure calculation using pruned transition trees, *Analytical Chemistry*, 87(11), 5738-5744. <https://doi.org/10.1021/acs.analchem.5b00941>

