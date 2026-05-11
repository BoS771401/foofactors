
<!-- README.md is generated from README.Rmd. Please edit that file -->

# foofactors

<!-- badges: start -->

<!-- badges: end -->

The goal of **foofactors** is to provide simple helper functions for
working with strings and factors.  
This package is created as part of an exercise following the *Whole
Game* workflow from the book **R Packages (2nd edition)**.

Currently, the package provides one main function:

- `str_split_one()` — a safer, more convenient wrapper around
  `stringr::str_split()` that always returns a character vector instead
  of a list.

## Installation

You can install the development version of **foofactors** from GitHub
with:

``` r
# install.packages("devtools")
devtools::install_github("YOUR_GITHUB_USERNAME/foofactors")
```

## Usage

A common task when working with strings is splitting a single string
into multiple pieces.  
Base R and stringr both return a list:

``` r
(x <- "alfa,bravo,charlie,delta")
#> [1] "alfa,bravo,charlie,delta"

strsplit(x, split = ",")
#> [[1]]
#> [1] "alfa"    "bravo"   "charlie" "delta"
stringr::str_split(x, pattern = ",")
#> [[1]]
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

`foofactors::str_split_one()` solves this by always returning a
character vector:

``` r
library(foofactors)

str_split_one(x, pattern = ",")
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

You can also use the `n` argument from stringr:

``` r
str_split_one(x, pattern = ",", n = 2)
#> [1] "alfa"                "bravo,charlie,delta"
```

And you can use stringr’s pattern helpers:

``` r
y <- "192.168.0.1"
str_split_one(y, pattern = stringr::fixed("."))
#> [1] "192" "168" "0"   "1"
```
