Lab9
================
Mafer Pérez
26 de octubre de 2019

``` r
library(twitteR)
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.5.3

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:twitteR':
    ## 
    ##     id, location

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(readr)
consumer_key <- "bSGZvIzT3ZsCBvINlUYA9inD6"
consumer_secret <- "BAVehNrJkmTGI0D05NyrlJRjTnzfvgvOXoLT6xE31FY2ZFrTiD"
access_token <- "828401502859456513-6RwSzpaposg3vZyJsRZY96aaD9Moo9D"
access_secret <- "gQ6FMYEL3dRw3q3lmDCWsCAw8TjFRjwcNU7riT2c6AIBT"
setup_twitter_oauth(consumer_key, consumer_secret, access_token, access_secret)
```

    ## [1] "Using direct authentication"

``` r
tw <- twitteR::searchTwitter('#Metoo', n = 1000, since = '2019-10-23', retryOnRateLimit = 1e3, lang="en")

df <- twitteR::twListToDF(tw)
df %>% head() %>% View()


write_csv(df,"tweets3.csv")
```