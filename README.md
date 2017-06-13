<!-- README.md is generated from README.Rmd. Please edit that file -->
ggpval
======

`ggpval` allow you to generate statistic test and add test p-value to plots automatically. P-valules can be presented as formated p-values or with stars (e.g. \*, \*\*). Alternatively one can also annotation groups with text.

Installation
------------

You can install latest version of ggpval from github with:

``` r
# install.packages("devtools")
devtools::install_github("s6juncheng/ggpval")
```

Stable versions are distributed on CRAN, install with:
```{r}
install.packages("ggpval")
```

Example
-------

Simulate data with groups.

``` r
library(ggpval)
library(data.table)
library(ggplot2)
A <- rnorm(200, 0, 3)
B <- rnorm(200, 2, 4)
G <- rep(c("G1", "G2"), each = 100)
dt <- data.table(A, B, G)
dt <- melt(dt, id.vars = "G")
```

A trivial boxplot example
-------------------------

Give group pairs you want to compare in `pairs`.

``` r
plt <- ggplot(dt, aes(variable, value)) +
  geom_boxplot() +
  geom_jitter()

add_pval(plt, pairs = list(c(1, 2)))
```

![](inst/image/README-unnamed-chunk-3-1.png)

Boxplot with facets
-------------------

``` r
plt <- ggplot(dt, aes(variable, value)) +
  geom_boxplot() +
  geom_jitter() +
  facet_wrap(~G)
add_pval(plt, pairs = list(c(1, 2)))
```

![](inst/image/README-unnamed-chunk-4-1.png)

Annotate your plot
------------------

``` r
add_pval(plt, pairs = list(c(1, 2)), annotation = "Awesome")
```

![](inst/image/README-unnamed-chunk-5-1.png)
