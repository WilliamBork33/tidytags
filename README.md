
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
#> Observations: 954
#> Variables: 88
#> $ user_id                 <chr> "888451225192214528", "27845032", "27845…
#> $ status_id               <chr> "1116713555900948481", "1116728725259812…
#> $ created_at              <dttm> 2019-04-12 14:43:53, 2019-04-12 15:44:1…
#> $ screen_name             <chr> "DrJMatth", "bod0ng", "bod0ng", "bod0ng"…
#> $ text                    <chr> "Thanks to those who attended the @AERA_…
#> $ source                  <chr> "Twitter for Android", "TweetDeck", "Twi…
#> $ display_text_width      <dbl> 140, 92, 140, 140, 140, 144, 278, 276, 1…
#> $ reply_to_status_id      <chr> NA, "1116595566098538500", NA, NA, NA, N…
#> $ reply_to_user_id        <chr> NA, "557044797", NA, NA, NA, NA, NA, NA,…
#> $ reply_to_screen_name    <chr> NA, "ShibaniAntonett", NA, NA, NA, NA, N…
#> $ is_quote                <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE…
#> $ is_retweet              <lgl> TRUE, FALSE, TRUE, TRUE, TRUE, TRUE, FAL…
#> $ favorite_count          <int> 0, 0, 0, 0, 0, 0, 7, 1, 0, 0, 0, 0, 0, 0…
#> $ retweet_count           <int> 3, 0, 3, 2, 7, 7, 0, 0, 3, 3, 3, 6, 4, 7…
#> $ hashtags                <list> ["aera19", "AERA19", <"AERA19", "Lesson…
#> $ symbols                 <list> [NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
#> $ urls_url                <list> [NA, "bit.ly/2Iu5ReS", NA, NA, NA, NA, …
#> $ urls_t.co               <list> [NA, "https://t.co/sNd00gFx4z", NA, NA,…
#> $ urls_expanded_url       <list> [NA, "http://bit.ly/2Iu5ReS", NA, NA, N…
#> $ media_url               <list> [NA, NA, NA, NA, NA, NA, NA, "http://pb…
#> $ media_t.co              <list> [NA, NA, NA, NA, NA, NA, NA, "https://t…
#> $ media_expanded_url      <list> [NA, NA, NA, NA, NA, NA, NA, "https://t…
#> $ media_type              <list> [NA, NA, NA, NA, NA, NA, NA, "photo", N…
#> $ ext_media_url           <list> [NA, NA, NA, NA, NA, NA, NA, "http://pb…
#> $ ext_media_t.co          <list> [NA, NA, NA, NA, NA, NA, NA, "https://t…
#> $ ext_media_expanded_url  <list> [NA, NA, NA, NA, NA, NA, NA, "https://t…
#> $ ext_media_type          <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ mentions_user_id        <list> [<"986433396187557895", "97910594805161…
#> $ mentions_screen_name    <list> [<"AKoenka", "AERA_MotSIG", "emilyqr">,…
#> $ lang                    <chr> "en", "en", "en", "en", "en", "en", "en"…
#> $ quoted_status_id        <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_text             <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_created_at       <dttm> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
#> $ quoted_source           <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_favorite_count   <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_retweet_count    <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_user_id          <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_screen_name      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_name             <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_followers_count  <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_friends_count    <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_statuses_count   <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_location         <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_description      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ quoted_verified         <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ retweet_status_id       <chr> "1116710937917034498", NA, "111591890323…
#> $ retweet_text            <chr> "Thanks to those who attended the @AERA_…
#> $ retweet_created_at      <dttm> 2019-04-12 14:33:29, NA, 2019-04-10 10:…
#> $ retweet_source          <chr> "Twitter for iPhone", NA, "Twitter for i…
#> $ retweet_favorite_count  <int> 24, NA, 9, 7, 10, 6, NA, NA, 16, 6, 7, 6…
#> $ retweet_retweet_count   <int> 3, NA, 3, 2, 7, 7, NA, NA, 3, 3, 3, 6, 4…
#> $ retweet_user_id         <chr> "986433396187557895", NA, "1852757365", …
#> $ retweet_screen_name     <chr> "AKoenka", NA, "JackmanICS", "JackmanICS…
#> $ retweet_name            <chr> "Alison Koenka", NA, "JackmanICS LabScho…
#> $ retweet_followers_count <int> 334, NA, 893, 893, 893, 7165, NA, NA, 26…
#> $ retweet_friends_count   <int> 521, NA, 5, 5, 5, 1419, NA, NA, 380, 205…
#> $ retweet_statuses_count  <int> 461, NA, 2470, 2470, 2470, 22500, NA, NA…
#> $ retweet_location        <chr> "Columbus, OH", NA, "Toronto", "Toronto"…
#> $ retweet_description     <chr> "Postdoc at Ohio State, educational and …
#> $ retweet_verified        <lgl> FALSE, NA, FALSE, FALSE, FALSE, TRUE, NA…
#> $ place_url               <chr> NA, NA, NA, NA, NA, NA, "https://api.twi…
#> $ place_name              <chr> NA, NA, NA, NA, NA, NA, "Lubbock", NA, N…
#> $ place_full_name         <chr> NA, NA, NA, NA, NA, NA, "Lubbock, TX", N…
#> $ place_type              <chr> NA, NA, NA, NA, NA, NA, "city", NA, NA, …
#> $ country                 <chr> NA, NA, NA, NA, NA, NA, "United States",…
#> $ country_code            <chr> NA, NA, NA, NA, NA, NA, "US", NA, NA, NA…
#> $ geo_coords              <list> [<NA, NA>, <NA, NA>, <NA, NA>, <NA, NA>…
#> $ coords_coords           <list> [<NA, NA>, <NA, NA>, <NA, NA>, <NA, NA>…
#> $ bbox_coords             <list> [<NA, NA, NA, NA, NA, NA, NA, NA>, <NA,…
#> $ status_url              <chr> "https://twitter.com/DrJMatth/status/111…
#> $ name                    <chr> "Jamaal Matthews", "Bodong Chen", "Bodon…
#> $ location                <chr> "", "Minneapolis, MN", "Minneapolis, MN"…
#> $ description             <chr> "Professor, Research Scientist in Psycho…
#> $ url                     <chr> NA, "https://t.co/SWocFqFPGi", "https://…
#> $ protected               <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE…
#> $ followers_count         <int> 503, 1209, 1209, 1209, 1209, 5138, 1130,…
#> $ friends_count           <int> 297, 1022, 1022, 1022, 1022, 450, 199, 1…
#> $ listed_count            <int> 3, 83, 83, 83, 83, 183, 61, 61, 0, 0, 0,…
#> $ statuses_count          <int> 792, 5758, 5758, 5758, 5758, 7965, 28722…
#> $ favourites_count        <int> 1256, 3820, 3820, 3820, 3820, 8386, 7749…
#> $ account_created_at      <dttm> 2017-07-21 17:30:53, 2009-03-31 10:07:1…
#> $ verified                <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE…
#> $ profile_url             <chr> NA, "https://t.co/SWocFqFPGi", "https://…
#> $ profile_expanded_url    <chr> NA, "http://meefen.github.io/", "http://…
#> $ account_lang            <chr> "en", "en", "en", "en", "en", "en", "en"…
#> $ profile_banner_url      <chr> "https://pbs.twimg.com/profile_banners/8…
#> $ profile_background_url  <chr> "http://abs.twimg.com/images/themes/them…
#> $ profile_image_url       <chr> "http://pbs.twimg.com/profile_images/888…
=======
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
glimpse(d1)
#> Observations: 30,586
#> Variables: 18
#> $ id_str                    <dbl> 1.116837e+18, 1.116828e+18, 1.116827e+…
#> $ from_user                 <chr> "JGUNNIII", "susanquinn1", "CarolCampb…
#> $ text                      <chr> "RT @MSUCEHS: Dean Tamara Lucas; TETD …
#> $ created_at                <chr> "Fri Apr 12 22:56:19 +0000 2019", "Fri…
#> $ time                      <chr> "12/04/2019 23:56:19", "12/04/2019 23:…
#> $ geo_coordinates           <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
#> $ user_lang                 <chr> "en", "en", "en", "en", "en", "en", "e…
#> $ in_reply_to_user_id_str   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
#> $ in_reply_to_screen_name   <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
#> $ from_user_id_str          <dbl> 5.497525e+08, 2.346572e+07, 3.006454e+…
#> $ in_reply_to_status_id_str <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
#> $ source                    <chr> "<a href=\"http://twitter.com\" rel=\"…
#> $ profile_image_url         <chr> "http://pbs.twimg.com/profile_images/9…
#> $ user_followers_count      <dbl> 167, 1754, 10810, 729, 248, 248, 2317,…
#> $ user_friends_count        <dbl> 653, 988, 2135, 488, 875, 875, 1417, 1…
#> $ user_location             <chr> NA, NA, "Toronto \U0001f1e8\U0001f1e6 …
#> $ status_url                <chr> "http://twitter.com/JGUNNIII/statuses/…
#> $ entities_str              <chr> "{\"hashtags\":[],\"symbols\":[],\"use…
=======
u <- rtweet::users_data(d)

dd <- add_users_data(edgelist, u)

dd
```

Future functionality
--------------------

-   We are looking to add geo-coding functionality
-   This package is new and we welcome contributors
