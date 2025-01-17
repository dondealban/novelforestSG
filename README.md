Data and Model from the Novel Forests of Singapore
================

<!-- README.md is generated from README.Rmd. Please edit that file -->
<!-- badges: start -->

[![](https://www.r-pkg.org/badges/version/novelforestSG?color=orange)](https://cran.r-project.org/package=novelforestSG)
[![](https://img.shields.io/badge/devel%20version-2.0.0-orange.svg)](https://github.com/hrlai/novelforestSG)
[![](https://img.shields.io/badge/doi-10.1111/avsc.12548-orange.svg)](https://doi.org/10.1111/avsc.12548)
[![License: CC BY
4.0](https://img.shields.io/badge/license-CC%20BY%204.0-blue.svg)](https://github.com/hrlai/novelforestSG/blob/master/LICENSE.md)
[![R build
status](https://github.com/hrlai/novelforestSG/workflows/R-CMD-check/badge.svg)](https://github.com/hrlai/novelforestSG/actions)
<!-- badges: end -->

# About

Welcome to the `R` package `novelforestSG`! It contains the raw forest
community data used in Lai et al. (2021), and also comprised part of the
raw data used in Neo et al. (2017).

In addition, it provides a `download_model()` function to download the
`brms` model fitted in Lai et al. (2021). Note that the model object
also contains input data that include the environmental variables of
forest plots (see below).

# Installation

From CRAN:

    install.packages("novelforestSG")

Or install the development version (especially if the devel version \>
CRAN version as stated above):

    install.packages("remotes")  # prerequisite
    remotes::install_github("hrlai/novelforestSG")

# Using the data

To access the raw data:

    library(novelforestSG)
    novelforest_data

For more information, see `?novelforest_data`.

To access the summarised data and environmental variables, first
download the model object. The model object is too large (16.5 MB) to
come with the package, but the `download_model` function will download
the model from our [GitHub development
website](https://github.com/hrlai/novelforestSG):

    mod <- download_model()

Then, extract the input data from the model object:

    in_dat <- mod$data

In the input/summarised data, you will find the environmental variables
as certain columns. These plot-level measurements can be matched to the
stem-level raw data via plot names. See `?download_model` for more
details.

Because the predictor variables were log-transformed and then scale to
zero mean and unit SD prior to modelling, you may wish to backtransform
them to their original scales, simply by:

    backtransform(in_dat)

# Dependencies

Because we analysed the data using the `brms` v2.10.0 package in `R`, it
is highly recommended that you [install
`brms`](https://github.com/paul-buerkner/brms) to squeeze the most out
of the model output:

    install.packages("brms")

You may also need `RTools` or `Xcode`, depending on your operating
system; see [the `brms`
homepage](https://github.com/paul-buerkner/brms#user-content-how-do-i-install-brms).
This will take a few minutes so have a cup of hot beverage handy.

# Issues

Please feel free to report any issues to [our GitHub Issue
page](https://github.com/hrlai/novelforestSG/issues).

# Erratum

While releasing additional data between v1.2.1 to v2.0.0, we realised
that some observations were removed by mistake in the original dataset
used in Lai et al. (2021). These omitted data are now included in
\>v2.0.0. We repeated the analysis using the corrected data in v2.0.0
and obtained extremely similar findings as reported Lai et al. (2021),
which is reassuring! Please feel free to contact us if you have any
concern.

# Citation

We believe that the sharing of datasets is important for advancing
ecology. When you use the data or model output in your original research
or meta-analysis, we appreciate if the following paper is cited:

> Lai, H. R., Tan, G. S. Y., Neo, L., Kee, C. Y., Yee, A. T. K., Tan, H.
> T. W., & Chong, K. Y. (2021). Decoupled responses of native and exotic
> tree diversities to distance from old-growth forest and soil
> phosphorus in novel secondary forests. *Applied Vegetation Science*,
> 24, e12548. doi: 10.1111/avsc.12548

See the
[LICENSE](https://github.com/hrlai/novelforestSG/blob/master/LICENSE.md)
file for license rights.

You may also be interested in a companion not-just-trees paper using
presence–absence data:

> Neo, L., Yee, A. T. K., Chong, K. Y., Kee, C. Y., & Tan, H. T. W.
> (2017). Vascular plant species richness and composition in two types
> of post-cultivation tropical secondary forest. *Applied Vegetation
> Science*, 20(4), 692–701. doi: 10.1111/avsc.12322

# Contacts

Hao Ran Lai <hrlai.ecology@gmail.com>  
Kwek Yan Chong <kwek@nus.edu.sg>  
Alex Thiam Koon Yee <alex_yee@nparks.gov.sg>
