Lab 03 - Nobel laureates
================
Haley Lam
Jan 30, 2026

### Load packages and data

``` r
library(tidyverse) 
```

``` r
nobel <- read_csv("data/nobel.csv")
```

## Exercises

### Exercise 1

``` r
nrow(nobel)
```

    ## [1] 935

``` r
ncol(nobel)
```

    ## [1] 26

``` r
head(nobel)
```

    ## # A tibble: 6 × 26
    ##      id firstname    surname  year category affiliation city  country born_date 
    ##   <dbl> <chr>        <chr>   <dbl> <chr>    <chr>       <chr> <chr>   <date>    
    ## 1     1 Wilhelm Con… Röntgen  1901 Physics  Munich Uni… Muni… Germany 1845-03-27
    ## 2     2 Hendrik A.   Lorentz  1902 Physics  Leiden Uni… Leid… Nether… 1853-07-18
    ## 3     3 Pieter       Zeeman   1902 Physics  Amsterdam … Amst… Nether… 1865-05-25
    ## 4     4 Henri        Becque…  1903 Physics  École Poly… Paris France  1852-12-15
    ## 5     5 Pierre       Curie    1903 Physics  École muni… Paris France  1859-05-15
    ## 6     6 Marie        Curie    1903 Physics  <NA>        <NA>  <NA>    1867-11-07
    ## # ℹ 17 more variables: died_date <date>, gender <chr>, born_city <chr>,
    ## #   born_country <chr>, born_country_code <chr>, died_city <chr>,
    ## #   died_country <chr>, died_country_code <chr>, overall_motivation <chr>,
    ## #   share <dbl>, motivation <chr>, born_country_original <chr>,
    ## #   born_city_original <chr>, died_country_original <chr>,
    ## #   died_city_original <chr>, city_original <chr>, country_original <chr>

The nobel dataset contains 935 observations and 26. Each row represents
one nobel prize winner.

### Exercise 2

``` r
nobel_living <- nobel %>%
  filter((is.na(died_date)), 
         (!is.na(country)),
         (gender != "org")
  )
```

There are now 228 observations of living nobel laureates.

### Exercise 3

``` r
nobel_living <- nobel_living %>%
  mutate(
    country_us = if_else(country == "USA", "USA", "Other")
  )
```

``` r
nobel_living_science <- nobel_living %>%
  filter(category %in% c("Physics", "Medicine", "Chemistry", "Economics"))
```

``` r
ggplot(data = nobel_living_science, aes(x = country_us)) +
  geom_bar() +
  facet_wrap(~ category) +
  coord_flip()
```

![](lab-03_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

Plot for category of a prize and whether they were in US.

Based on this, the BuzzFeed article is right, that over half were based
in the US when they won the nobel prize.

### Exercise 4

### Exercise 5

…

### Exercise 6

…
