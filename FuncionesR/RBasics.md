Functions in R
================
Mafer Pérez
29 de julio de 2019

Functions
---------

``` r
find_sample <- function(x) {
  for_index <- sample(1:nrow(x), size = 10, replace = FALSE)
  new_df <- x[for_index,]
  return(new_df)
}
data <- data.frame(
  a= 1:10,
  b= sample(c("GT", "US","CA"),size = 10, replace = TRUE )
)
find_sample(data)
```

    ##     a  b
    ## 8   8 CA
    ## 3   3 GT
    ## 5   5 CA
    ## 9   9 CA
    ## 6   6 GT
    ## 10 10 CA
    ## 2   2 CA
    ## 1   1 GT
    ## 7   7 US
    ## 4   4 GT

``` r
generate_df <-function(x) {
  df <- data.frame(
    a= sample(letters, size =10, replace=TRUE),
    b = sample(1:10, size=10, replace=TRUE)
  )
return(df)
}

generate_df(1)
```

    ##    a  b
    ## 1  i  2
    ## 2  i  3
    ## 3  q 10
    ## 4  y  8
    ## 5  s 10
    ## 6  b  3
    ## 7  k  8
    ## 8  e  6
    ## 9  t  8
    ## 10 u  4

``` r
result_list <- list()
system.time(for(i in 1:1000){
  result_list[[i]] <- generate_df(1)
})
```

    ##    user  system elapsed 
    ##    1.49    0.02    1.52

``` r
system.time(
  lapply(1:1000, generate_df)
)
```

    ##    user  system elapsed 
    ##    1.40    0.00    1.42
