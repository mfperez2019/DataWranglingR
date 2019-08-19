Clase3EXTRA
================
Mafer Pérez
12 de agosto de 2019

``` r
library(tidyverse)
```

    ## -- Attaching packages -------------------------------------- tidyverse 1.2.1 --

    ## v ggplot2 3.0.0     v purrr   0.2.5
    ## v tibble  2.1.3     v dplyr   0.8.3
    ## v tidyr   0.8.1     v stringr 1.3.1
    ## v readr   1.1.1     v forcats 0.3.0

    ## Warning: package 'tibble' was built under R version 3.5.3

    ## Warning: package 'dplyr' was built under R version 3.5.3

    ## -- Conflicts ----------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(readr)
players_score <- read_csv(file = "C:/Users/Mafer/Desktop/GitHub/DataWranglingR/Tidy/football-world-cup-2018-dataset/Players_Score.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   Rank = col_integer(),
    ##   player = col_character(),
    ##   club = col_character(),
    ##   age = col_integer(),
    ##   Apps = col_character(),
    ##   Mins = col_integer(),
    ##   Goals = col_character(),
    ##   Assists = col_character(),
    ##   Yel = col_character(),
    ##   Red = col_character(),
    ##   SpG = col_character(),
    ##   PS = col_double(),
    ##   AerialsWon = col_character(),
    ##   MotM = col_character(),
    ##   Rating = col_double()
    ## )

``` r
 view(players_score)

players_score$cambio<-str_extract_all(players_score$Apps, "\\([^)]*\\)","")
players_score$cambio<-str_extract_all(players_score$cambio,"[0-9]+")
players_score$Apps<-str_replace_all(players_score$Apps, "\\([^)]*\\)","")

### Volver todas las variables numericas a formato numerico
numbers <- c("age", "Apps", "cambio", "Goals", "Assists", "Yel", "Red", "SpG", "PS", "AerialsWon", "MotM", "Rating")
players_score[numbers] <- lapply(players_score[numbers], as.numeric)
```

    ## Warning in lapply(players_score[numbers], as.numeric): NAs introducidos por
    ## coerción

    ## Warning in lapply(players_score[numbers], as.numeric): NAs introducidos por
    ## coerción

    ## Warning in lapply(players_score[numbers], as.numeric): NAs introducidos por
    ## coerción

    ## Warning in lapply(players_score[numbers], as.numeric): NAs introducidos por
    ## coerción

    ## Warning in lapply(players_score[numbers], as.numeric): NAs introducidos por
    ## coerción

    ## Warning in lapply(players_score[numbers], as.numeric): NAs introducidos por
    ## coerción

    ## Warning in lapply(players_score[numbers], as.numeric): NAs introducidos por
    ## coerción

``` r
head(players_score) %>% view()

players_score[numbers] <- players_score[numbers] %>% replace_na(list(age=0, Goals=0, Assists=0, Yel=0, Red=0, SpG=0, PS=0, AerialsWon=0, MotM=0, Rating=0, cambio=0))
players_score
```

    ## # A tibble: 11,150 x 16
    ##     Rank player club    age  Apps  Mins Goals Assists   Yel   Red   SpG
    ##    <int> <chr>  <chr> <dbl> <dbl> <int> <dbl>   <dbl> <dbl> <dbl> <dbl>
    ##  1     1 Hakim~ Ajax     25    34  3043     9      15     4     0   4.9
    ##  2     2 Alire~ AZ A~    24    33  2840    21      12     3     0   4.3
    ##  3     3 Hirvi~ PSV ~    22    29  2350    17       8     4     2   3.4
    ##  4     4 David~ Ajax     21    28  2534    14      11     3     0   2.1
    ##  5     5 Steve~ Feye~    26    31  2597    18      12     5     1   2.9
    ##  6     6 Luuk ~ PSV ~    27    22  2078    12       5     1     0   3.4
    ##  7     7 Brand~ Hera~    25    29  2497     5      13     1     0   2.2
    ##  8     8 Marco~ PSV ~    25    28  2483    14       4     4     0   2.8
    ##  9     9 Justi~ Ajax     19    27  2335    10       5     2     0   2.7
    ## 10    10 Zakar~ FC U~    25    31  2755    15      10     8     0   3.3
    ## # ... with 11,140 more rows, and 5 more variables: PS <dbl>,
    ## #   AerialsWon <dbl>, MotM <dbl>, Rating <dbl>, cambio <dbl>

``` r
###filter
filter(players_score, club=="Real Madrid", age <30)
```

    ## # A tibble: 41 x 16
    ##     Rank player club    age  Apps  Mins Goals Assists   Yel   Red   SpG
    ##    <int> <chr>  <chr> <dbl> <dbl> <int> <dbl>   <dbl> <dbl> <dbl> <dbl>
    ##  1     5 Casem~ Real~    26    30  2601     5       3     8     0   1.1
    ##  2     6 Garet~ Real~    28    20  1803    16       2     5     0   3  
    ##  3     8 Toni ~ Real~    28    26  2268     5       7     4     0   1.5
    ##  4    26 Isco   Real~    26    21  1781     7       7     1     0   1.6
    ##  5    26 Isco   Real~    26    21  1781     7       7     1     0   1.6
    ##  6    45 Danie~ Real~    26    25  2223     0       2    11     1   0.5
    ##  7    45 Danie~ Real~    26    25  2223     0       2    11     1   0.5
    ##  8    52 Marco~ Real~    22    19  1839     6       6     2     0   1.8
    ##  9    52 Marco~ Real~    22    19  1839     6       6     2     0   1.8
    ## 10    84 Lucas~ Real~    26    16  1670     4       7     3     0   1  
    ## # ... with 31 more rows, and 5 more variables: PS <dbl>, AerialsWon <dbl>,
    ## #   MotM <dbl>, Rating <dbl>, cambio <dbl>

``` r
filter(players_score, club %in% c("Real Madrid", "Barcelona", age <30))
```

    ## # A tibble: 115 x 16
    ##     Rank player club    age  Apps  Mins Goals Assists   Yel   Red   SpG
    ##    <int> <chr>  <chr> <dbl> <dbl> <int> <dbl>   <dbl> <dbl> <dbl> <dbl>
    ##  1     1 Lione~ Barc~    30    32  2997    34      12     3     0   5.5
    ##  2     2 Crist~ Real~    33    27  2293    26       5     1     0   6.6
    ##  3     3 Luis ~ Barc~    31    32  2902    25      12     9     0   3.7
    ##  4     4 Couti~ Barc~    25    16  1304     8       5     1     0   2.1
    ##  5     5 Casem~ Real~    26    30  2601     5       3     8     0   1.1
    ##  6     6 Garet~ Real~    28    20  1803    16       2     5     0   3  
    ##  7     8 Toni ~ Real~    28    26  2268     5       7     4     0   1.5
    ##  8    15 Luka ~ Real~    32    23  1976     1       6     3     0   1.3
    ##  9    16 Sergi~ Barc~    29    30  2600     1       4     8     0   0.2
    ## 10    18 Jordi~ Barc~    29    30  2745     2       8     8     0   0.5
    ## # ... with 105 more rows, and 5 more variables: PS <dbl>,
    ## #   AerialsWon <dbl>, MotM <dbl>, Rating <dbl>, cambio <dbl>

``` r
###prmer filtro pero con pope
players_score %>% 
  filter(club=="Real Madrid")
```

    ## # A tibble: 63 x 16
    ##     Rank player club    age  Apps  Mins Goals Assists   Yel   Red   SpG
    ##    <int> <chr>  <chr> <dbl> <dbl> <int> <dbl>   <dbl> <dbl> <dbl> <dbl>
    ##  1     2 Crist~ Real~    33    27  2293    26       5     1     0   6.6
    ##  2     5 Casem~ Real~    26    30  2601     5       3     8     0   1.1
    ##  3     6 Garet~ Real~    28    20  1803    16       2     5     0   3  
    ##  4     8 Toni ~ Real~    28    26  2268     5       7     4     0   1.5
    ##  5    15 Luka ~ Real~    32    23  1976     1       6     3     0   1.3
    ##  6    15 Luka ~ Real~    32    23  1976     1       6     3     0   1.3
    ##  7    26 Isco   Real~    26    21  1781     7       7     1     0   1.6
    ##  8    26 Isco   Real~    26    21  1781     7       7     1     0   1.6
    ##  9    40 Sergi~ Real~    32    26  2292     4       1     7     2   1.1
    ## 10    40 Sergi~ Real~    32    26  2292     4       1     7     2   1.1
    ## # ... with 53 more rows, and 5 more variables: PS <dbl>, AerialsWon <dbl>,
    ## #   MotM <dbl>, Rating <dbl>, cambio <dbl>

``` r
###Seleccionamos unicamente las columnas de club, edad y filtreamos por club
filter(select(players_score,club,age), club=="Real Madrid")
```

    ## # A tibble: 63 x 2
    ##    club          age
    ##    <chr>       <dbl>
    ##  1 Real Madrid    33
    ##  2 Real Madrid    26
    ##  3 Real Madrid    28
    ##  4 Real Madrid    28
    ##  5 Real Madrid    32
    ##  6 Real Madrid    32
    ##  7 Real Madrid    26
    ##  8 Real Madrid    26
    ##  9 Real Madrid    32
    ## 10 Real Madrid    32
    ## # ... with 53 more rows

``` r
##Seleccionemos únicamente las columnas de club y edad y filtremos por club
players_score %>% 
  select(club,age) %>% 
  filter(club== "Real Madrid")
```

    ## # A tibble: 63 x 2
    ##    club          age
    ##    <chr>       <dbl>
    ##  1 Real Madrid    33
    ##  2 Real Madrid    26
    ##  3 Real Madrid    28
    ##  4 Real Madrid    28
    ##  5 Real Madrid    32
    ##  6 Real Madrid    32
    ##  7 Real Madrid    26
    ##  8 Real Madrid    26
    ##  9 Real Madrid    32
    ## 10 Real Madrid    32
    ## # ... with 53 more rows

``` r
##Rate entre minuto sobre goal
players_score %>% 
  mutate(Goal_Rate = Mins/Goals) %>% 
  arrange(desc(Goal_Rate))
```

    ## # A tibble: 11,150 x 17
    ##     Rank player club    age  Apps  Mins Goals Assists   Yel   Red   SpG
    ##    <int> <chr>  <chr> <dbl> <dbl> <int> <dbl>   <dbl> <dbl> <dbl> <dbl>
    ##  1    21 Frenk~ Ajax     21    16  1560     0       7     2     0   0.5
    ##  2    21 Frenk~ Ajax     21    16  1560     0       7     2     0   0.5
    ##  3    46 Alexa~ Vite~    29    19  1709     0       8     3     0   1  
    ##  4    47 Jurge~ Exce~    25    33  2970     0       2     7     0   0.7
    ##  5    48 Kevin~ Feye~    21    18  1694     0       4     1     0   0.8
    ##  6    46 Alexa~ Vite~    29    19  1709     0       8     3     0   1  
    ##  7    47 Jurge~ Exce~    25    33  2970     0       2     7     0   0.7
    ##  8    48 Kevin~ Feye~    21    18  1694     0       4     1     0   0.8
    ##  9    54 Sergi~ FC G~    28    34  3060     0       0     1     0   0  
    ## 10    54 Sergi~ FC G~    28    34  3060     0       0     1     0   0  
    ## # ... with 11,140 more rows, and 6 more variables: PS <dbl>,
    ## #   AerialsWon <dbl>, MotM <dbl>, Rating <dbl>, cambio <dbl>,
    ## #   Goal_Rate <dbl>

``` r
##Una posible Solución
players_score %>% 
  filter(Goals > 0) %>% 
  mutate(Goal_Rate = Mins/Goals) %>% 
  arrange(desc(Goal_Rate)) %>% 
  distinct()
```

    ## # A tibble: 3,199 x 17
    ##     Rank player club    age  Apps  Mins Goals Assists   Yel   Red   SpG
    ##    <int> <chr>  <chr> <dbl> <dbl> <int> <dbl>   <dbl> <dbl> <dbl> <dbl>
    ##  1     2 Curti~ Derby    33    48  4313     1       3     2     0   0.5
    ##  2    68 Tim R~ Fulh~    30    47  4230     1       0     2     0   0.1
    ##  3   149 Ben G~ Midd~    25    47  4230     1       3     6     0   0.4
    ##  4   307 Chris~ Read~    28    46  4126     1       1     6     0   0.3
    ##  5   173 Conor~ Wolv~    25    45  3975     1       2     4     1   0  
    ##  6   152 Enda ~ Shef~    27    45  3973     1       4     9     0   0.2
    ##  7    44 Mark ~ Bolt~    28    44  3960     1       0    10     0   0.4
    ##  8    58 Paul ~ Pres~    30    44  3916     1       2    10     0   0.9
    ##  9   256 Korey~ Bris~    27    44  3909     1       1     4     0   0.5
    ## 10    48 Richa~ Derby    31    44  3878     1       5     4     0   0.5
    ## # ... with 3,189 more rows, and 6 more variables: PS <dbl>,
    ## #   AerialsWon <dbl>, MotM <dbl>, Rating <dbl>, cambio <dbl>,
    ## #   Goal_Rate <dbl>

``` r
###equipo goleador
players_score %>% 
  select(club, Goals) %>% 
  group_by(club) %>% 
  summarise(team_goals = sum(Goals)) %>% 
  arrange(desc(team_goals))
```

    ## # A tibble: 332 x 2
    ##    club                team_goals
    ##    <chr>                    <dbl>
    ##  1 Ajax                       206
    ##  2 Lazio                      199
    ##  3 Paris Saint Germain        179
    ##  4 Vitesse                    176
    ##  5 Manchester City            173
    ##  6 Lyon                       168
    ##  7 Real Madrid                167
    ##  8 Braga                      164
    ##  9 Marseille                  164
    ## 10 PSV Eindhoven              164
    ## # ... with 322 more rows

``` r
players_score %>% 
  select(player, PS, club)
```

    ## # A tibble: 11,150 x 3
    ##    player                 PS club         
    ##    <chr>               <dbl> <chr>        
    ##  1 Hakim Ziyech         75.4 Ajax         
    ##  2 Alireza Jahanbakhsh  73.4 AZ Alkmaar   
    ##  3 Hirving Lozano       75.3 PSV Eindhoven
    ##  4 David Neres          83.1 Ajax         
    ##  5 Steven Berghuis      78.4 Feyenoord    
    ##  6 Luuk de Jong         66.7 PSV Eindhoven
    ##  7 Brandley Kuwas       76.9 Heracles     
    ##  8 Marco van Ginkel     79.4 PSV Eindhoven
    ##  9 Justin Kluivert      86.7 Ajax         
    ## 10 Zakaria Labyad       72.5 FC Utrecht   
    ## # ... with 11,140 more rows

``` r
#### AQUI  EMPIEZA LO EXTRA
#1 Quien es el jugador con el mejor porcentaje de pase y de cual club es
view(players_score)
players_score %>% 
  select(player,club,PS ) %>% 
  arrange(desc(PS)) %>% 
  distinct() 
```

    ## # A tibble: 5,585 x 3
    ##    player           club                   PS
    ##    <chr>            <chr>               <dbl>
    ##  1 Thiago Silva     Paris Saint Germain  96.1
    ##  2 Dante            Nice                 96  
    ##  3 Nampalys Mendy   Nice                 95.9
    ##  4 Arthur           Gremio               95.8
    ##  5 Omer Toprak      Borussia Dortmund    95.7
    ##  6 John Stones      Manchester City      95.5
    ##  7 Vincent Koziello Nice                 95.4
    ##  8 Esteban Pavez    Atletico PR          95.4
    ##  9 Presnel Kimpembe Paris Saint Germain  95.3
    ## 10 Thiago Silva     Paris Saint Germain  94.9
    ## # ... with 5,575 more rows

``` r
#Respuesta: Thiago Silva de     Paris Saint Germain con un PS de 96.1

#2 Quien es el jugador que mas veces ha sido Man of Match y su indice de goles por minuto
players_score %>% 
  select(player,MotM,Goals,Mins ) %>% 
  mutate(Golespormin = Goals/Mins) %>% 
  arrange(desc(MotM)) %>% 
  distinct()
```

    ## # A tibble: 5,584 x 5
    ##    player               MotM Goals  Mins Golespormin
    ##    <chr>               <dbl> <dbl> <int>       <dbl>
    ##  1 Lionel Messi           22    34  2997    0.0113  
    ##  2 Alireza Jahanbakhsh    14    21  2840    0.00739 
    ##  3 Adama Traore           14     5  2427    0.00206 
    ##  4 Florian Thauvin        13    22  2966    0.00742 
    ##  5 Neymar                 12    19  1788    0.0106  
    ##  6 Nabil Fekir            12    18  2481    0.00726 
    ##  7 Iago Aspas             11    22  2938    0.00749 
    ##  8 Jonas                  11    34  2473    0.0137  
    ##  9 Curtis Davies          10     1  4313    0.000232
    ## 10 Hakim Ziyech            9     9  3043    0.00296 
    ## # ... with 5,574 more rows

``` r
# RESPUESTA: Lionel Messi   que ha sido 22 veces MoM     y su indice es de  0.0113446780

#3 Quien es el jugador mas joven con mas goles anotados a traves de todo el set de datos
players_score %>% 
  select(player,age,Goals ) %>% 
  arrange(age) %>% 
  distinct()
```

    ## # A tibble: 5,399 x 3
    ##    player             age Goals
    ##    <chr>            <dbl> <dbl>
    ##  1 Kik Pierie          17     0
    ##  2 Rodrygo             17     5
    ##  3 Vinicius Junior     17     4
    ##  4 Alphonso Davies     17     1
    ##  5 Matthijs de Ligt    18     3
    ##  6 Deroy Duarte        18     3
    ##  7 Ryan Sessegnon      18    16
    ##  8 Joe Willock         18     0
    ##  9 Boubacar Kamara     18     0
    ## 10 Reiss Nelson        18     0
    ## # ... with 5,389 more rows

``` r
#RESPUESTA: Rodrygo de 17 años con 5 goles

#4 Quien es el jugador que entra de cambio mas efectivo al momento de anotar goles
players_score %>% 
  select(player,Mins,Goals ) %>% 
  arrange((Mins)) %>% 
  distinct()
```

    ## # A tibble: 5,584 x 3
    ##    player             Mins Goals
    ##    <chr>             <int> <dbl>
    ##  1 Sun Jungang          15     0
    ##  2 Zhao Mingyu          20     0
    ##  3 Andreas Cornelius    25     2
    ##  4 Uros Racic           25     0
    ##  5 Ivan Saponjic        26     0
    ##  6 Dentinho             34     0
    ##  7 Yang Wanshun         35     0
    ##  8 Dani Quintana        39     0
    ##  9 Viktor Kovalenko     43     0
    ## 10 Matheus Galdezani    48     0
    ## # ... with 5,574 more rows

``` r
#Respuesta:  Andreas Cornelius y anota 2 goles.

#5. Quien es el jugador que es mas sucio

players_score %>% 
  select(player,Yel,Red ) %>% 
  filter(Red >2) %>% 
  arrange(desc(Yel)) %>% 
  distinct()
```

    ## # A tibble: 5 x 3
    ##   player            Yel   Red
    ##   <chr>           <dbl> <dbl>
    ## 1 Hassan Yebda        7     3
    ## 2 Dusko Tosic         7     3
    ## 3 Marcao              5     3
    ## 4 Gaetano Berardi     3     3
    ## 5 Prince              2     3

``` r
# De los jugadores con 2 tarjetas rojas,  Hassan Yebda y Dusko Tosic que más tarjetas amarillas

#6. Cual es el mejor equipo de todos
players_score %>% 
  select(club,Goals) %>% 
  arrange(desc(Goals)) %>% 
  distinct()
```

    ## # A tibble: 1,985 x 2
    ##    club                Goals
    ##    <chr>               <dbl>
    ##  1 Barcelona              34
    ##  2 Benfica                34
    ##  3 Liverpool              32
    ##  4 Tottenham              30
    ##  5 Bayern Munich          29
    ##  6 Galatasaray            29
    ##  7 Lazio                  29
    ##  8 Inter                  29
    ##  9 Paris Saint Germain    28
    ## 10 Sporting CP            27
    ## # ... with 1,975 more rows

``` r
#RESPUESTA: Barcelona tienen más goles
```
