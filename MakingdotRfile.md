MakingdotRfile.R
================
HANEDI
2020-01-27

``` r
# Determine the bug when you run `get_climates()`
# Hint: Use `traceback()` to find where it occurs, add breakpoints / `browser()` calls
# Hint: look at types of input

library(tidyverse)
```

    ## Warning: package 'tidyverse' was built under R version 3.6.2

    ## -- Attaching packages ---------------------------------------------- tidyverse 1.3.0 --

    ## v ggplot2 3.2.1     v purrr   0.3.3
    ## v tibble  2.1.3     v dplyr   0.8.3
    ## v tidyr   1.0.0     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.4.0

    ## Warning: package 'ggplot2' was built under R version 3.6.2

    ## Warning: package 'tibble' was built under R version 3.6.2

    ## Warning: package 'tidyr' was built under R version 3.6.2

    ## Warning: package 'readr' was built under R version 3.6.2

    ## Warning: package 'purrr' was built under R version 3.6.2

    ## Warning: package 'dplyr' was built under R version 3.6.2

    ## Warning: package 'stringr' was built under R version 3.6.2

    ## Warning: package 'forcats' was built under R version 3.6.2

    ## -- Conflicts ------------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
# Separate, flatten, and trim values in the vector
clean <- function(vec) {
  #browser()
  recover()
  values <- strsplit(vec,",")
  flat_values <- unlist(values)
  trimmed_values <- str_trim(flat_values)
  trimmed_values
}

# Clean vector and get the unique values
uniquify <- function(vec) {
  clean_values <- clean(vec)
  unique_values <- unique(clean_values)
  unique_values
}

##adding a comment and testing commit

# Read data and get unique climate values
get_climates <- function() {
  planets <- read.csv2(here::here("planets.csv"),stringsAsFactors = FALSE)
  unique_climate <- uniquify(planets$climate)
  unique_climate
}

# This example originally used in Amanda Gadrow's excellent debugging talk at rstudio::conf 2018,
# https://github.com/ajmcoqui/debuggingRStudio/blob/b70a3575a3ff5e7867b05fb5e84568abba426c4b/error_example.R
```
