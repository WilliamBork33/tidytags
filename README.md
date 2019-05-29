
<!-- README.md is generated from README.Rmd. Please edit that file -->
rTAGS
=====

The goal of rTAGS is to make it easy to work with Twitter data collected via [TAGS](https://tags.hawksey.info/) in R. This package makes ample use of the [{rtweet} package](https://rtweet.info/) to process and prepare the data.

Installation
------------

You can install the released version of rTAGS from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("devtools")
devtools::install_github('bretsw/rTAGS)
```

Example
-------

This is a basic example which shows you how to read a TAGS sheet and then use {rtweet} (via `pull_data()`) to access additional data.

``` r
library(rTAGS)
library(tidyverse)

# googlesheets::gs_auth()

d <- "https://docs.google.com/spreadsheets/d/1KZBbO0JB4PySzaeBMzHHgBB0DR8IgEeeg6YpK_oA6ko/edit?usp=sharing" %>%
        read_tags() %>% 
        pull_data()
```

Here is the result:

``` r
glimpse(d)
```

Creating an edgelist from the TAGS data
---------------------------------------

``` r
edgelist <- create_edgelist(d)

edgelist %>% 
  count(edge_type)
```

If you want to simply view the TAGS archive, you can use `read_tags()`:

``` r
d1 <- "https://docs.google.com/spreadsheets/d/1WM2xWG9B0Wqn3YG5uakfy_NSAEzIFP2nEAJ5U_fqufc/edit#gid=8743918" %>% 
        read_tags()
```

Other functionality
-------------------

-   We are working to add gender coding (see `gender-coding.R` for a worked example).

### Adding user data

-   We also have functionality to add user-level data to an edgelist (see `add-users-data-.R`)

``` r
u <- rtweet::users_data(d)

dd <- add_users_data(edgelist, u)

dd
```

Future functionality
--------------------

-   We are looking to add geo-coding functionality
-   This package is new and we welcome contributors
