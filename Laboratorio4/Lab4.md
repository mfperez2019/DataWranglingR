Laboratorio4
================
Mafer Pérez
28 de agosto de 2019

``` r
library(tidyr)
library(reshape2)
```

    ## 
    ## Attaching package: 'reshape2'

    ## The following object is masked from 'package:tidyr':
    ## 
    ##     smiths

``` r
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.5.3

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(stringr)
#ejercicio de la clase
df <- data.frame(row= LETTERS[1:3], a= 1:3, b= 4:6, c=7:9)
df
```

    ##   row a b c
    ## 1   A 1 4 7
    ## 2   B 2 5 8
    ## 3   C 3 6 9

``` r
#melt de reshape2
dfm <- melt(df, id= "row")

#gather de Tidyr
dfg <- gather(df, key="variable", value= "value", a:c)
dfg
```

    ##   row variable value
    ## 1   A        a     1
    ## 2   B        a     2
    ## 3   C        a     3
    ## 4   A        b     4
    ## 5   B        b     5
    ## 6   C        b     6
    ## 7   A        c     7
    ## 8   B        c     8
    ## 9   C        c     9

``` r
colnames(dfg) <- c("row", "letras", "valores")
dfg
```

    ##   row letras valores
    ## 1   A      a       1
    ## 2   B      a       2
    ## 3   C      a       3
    ## 4   A      b       4
    ## 5   B      b       5
    ## 6   C      b       6
    ## 7   A      c       7
    ## 8   B      c       8
    ## 9   C      c       9

``` r
library(plyr)
library(readr)
raw <- read_csv(file = "raw.csv") %>% select(-X1)
```

    ## Warning: Missing column names filled in: 'X1' [1]

    ## Parsed with column specification:
    ## cols(
    ##   X1 = col_integer(),
    ##   country = col_character(),
    ##   year = col_integer(),
    ##   m014 = col_integer(),
    ##   m1524 = col_integer(),
    ##   m2534 = col_integer(),
    ##   m3544 = col_integer(),
    ##   m4554 = col_integer(),
    ##   m5564 = col_integer(),
    ##   m65 = col_integer(),
    ##   mu = col_character(),
    ##   f014 = col_integer(),
    ##   f1524 = col_integer(),
    ##   f2534 = col_integer(),
    ##   f3544 = col_integer(),
    ##   f4554 = col_integer(),
    ##   f5564 = col_integer(),
    ##   f65 = col_integer(),
    ##   fu = col_character()
    ## )

``` r
raw$mu <- NULL
raw$fu <- NULL
raw <- gather(raw, key="age", value ="freq" , m014:f65) %>% arrange(country)
#raw <- na.omit(raw)
raw$sexo <- str_sub(raw$age, start = 1, end = 1)
raw$edad <- str_sub(raw$age, start=2)
raw$edad <- revalue(raw$edad, c('014' = "0-14", '1524' = "15-24", '2534' = "25-34", '3544' = "35-44", '4554' = "45-54", '5564' = "55-64", '65' = "65+"))
raw1 <- raw %>% select(country, year, sexo, edad, freq)
raw1$head
```

    ## Warning: Unknown or uninitialised column: 'head'.

    ## NULL

``` r
load(file = "wide_religion.rda")
religion <- gather(wide_religion, key="income", value ="freq", '<$10k':"Don't know/refused") %>% arrange(religion)
religion
```

    ##                    religion             income freq
    ## 1                  Agnostic              <$10k   27
    ## 2                  Agnostic            $10-20k   34
    ## 3                  Agnostic            $20-30k   60
    ## 4                  Agnostic            $30-40k   81
    ## 5                  Agnostic            $40-50k   76
    ## 6                  Agnostic            $50-75k  137
    ## 7                  Agnostic           $75-100k  122
    ## 8                  Agnostic          $100-150k  109
    ## 9                  Agnostic              >150k   84
    ## 10                 Agnostic Don't know/refused   96
    ## 11                  Atheist              <$10k   12
    ## 12                  Atheist            $10-20k   27
    ## 13                  Atheist            $20-30k   37
    ## 14                  Atheist            $30-40k   52
    ## 15                  Atheist            $40-50k   35
    ## 16                  Atheist            $50-75k   70
    ## 17                  Atheist           $75-100k   73
    ## 18                  Atheist          $100-150k   59
    ## 19                  Atheist              >150k   74
    ## 20                  Atheist Don't know/refused   76
    ## 21                 Buddhist              <$10k   27
    ## 22                 Buddhist            $10-20k   21
    ## 23                 Buddhist            $20-30k   30
    ## 24                 Buddhist            $30-40k   34
    ## 25                 Buddhist            $40-50k   33
    ## 26                 Buddhist            $50-75k   58
    ## 27                 Buddhist           $75-100k   62
    ## 28                 Buddhist          $100-150k   39
    ## 29                 Buddhist              >150k   53
    ## 30                 Buddhist Don't know/refused   54
    ## 31                 Catholic              <$10k  418
    ## 32                 Catholic            $10-20k  617
    ## 33                 Catholic            $20-30k  732
    ## 34                 Catholic            $30-40k  670
    ## 35                 Catholic            $40-50k  638
    ## 36                 Catholic            $50-75k 1116
    ## 37                 Catholic           $75-100k  949
    ## 38                 Catholic          $100-150k  792
    ## 39                 Catholic              >150k  633
    ## 40                 Catholic Don't know/refused 1489
    ## 41       Dont know/refused              <$10k   15
    ## 42       Dont know/refused            $10-20k   14
    ## 43       Dont know/refused            $20-30k   15
    ## 44       Dont know/refused            $30-40k   11
    ## 45       Dont know/refused            $40-50k   10
    ## 46       Dont know/refused            $50-75k   35
    ## 47       Dont know/refused           $75-100k   21
    ## 48       Dont know/refused          $100-150k   17
    ## 49       Dont know/refused              >150k   18
    ## 50       Dont know/refused Don't know/refused  116
    ## 51         Evangelical Prot              <$10k  575
    ## 52         Evangelical Prot            $10-20k  869
    ## 53         Evangelical Prot            $20-30k 1064
    ## 54         Evangelical Prot            $30-40k  982
    ## 55         Evangelical Prot            $40-50k  881
    ## 56         Evangelical Prot            $50-75k 1486
    ## 57         Evangelical Prot           $75-100k  949
    ## 58         Evangelical Prot          $100-150k  723
    ## 59         Evangelical Prot              >150k  414
    ## 60         Evangelical Prot Don't know/refused 1529
    ## 61                    Hindu              <$10k    1
    ## 62                    Hindu            $10-20k    9
    ## 63                    Hindu            $20-30k    7
    ## 64                    Hindu            $30-40k    9
    ## 65                    Hindu            $40-50k   11
    ## 66                    Hindu            $50-75k   34
    ## 67                    Hindu           $75-100k   47
    ## 68                    Hindu          $100-150k   48
    ## 69                    Hindu              >150k   54
    ## 70                    Hindu Don't know/refused   37
    ## 71  Historically Black Prot              <$10k  228
    ## 72  Historically Black Prot            $10-20k  244
    ## 73  Historically Black Prot            $20-30k  236
    ## 74  Historically Black Prot            $30-40k  238
    ## 75  Historically Black Prot            $40-50k  197
    ## 76  Historically Black Prot            $50-75k  223
    ## 77  Historically Black Prot           $75-100k  131
    ## 78  Historically Black Prot          $100-150k   81
    ## 79  Historically Black Prot              >150k   78
    ## 80  Historically Black Prot Don't know/refused  339
    ## 81        Jehovah's Witness              <$10k   20
    ## 82        Jehovah's Witness            $10-20k   27
    ## 83        Jehovah's Witness            $20-30k   24
    ## 84        Jehovah's Witness            $30-40k   24
    ## 85        Jehovah's Witness            $40-50k   21
    ## 86        Jehovah's Witness            $50-75k   30
    ## 87        Jehovah's Witness           $75-100k   15
    ## 88        Jehovah's Witness          $100-150k   11
    ## 89        Jehovah's Witness              >150k    6
    ## 90        Jehovah's Witness Don't know/refused   37
    ## 91                   Jewish              <$10k   19
    ## 92                   Jewish            $10-20k   19
    ## 93                   Jewish            $20-30k   25
    ## 94                   Jewish            $30-40k   25
    ## 95                   Jewish            $40-50k   30
    ## 96                   Jewish            $50-75k   95
    ## 97                   Jewish           $75-100k   69
    ## 98                   Jewish          $100-150k   87
    ## 99                   Jewish              >150k  151
    ## 100                  Jewish Don't know/refused  162
    ## 101           Mainline Prot              <$10k  289
    ## 102           Mainline Prot            $10-20k  495
    ## 103           Mainline Prot            $20-30k  619
    ## 104           Mainline Prot            $30-40k  655
    ## 105           Mainline Prot            $40-50k  651
    ## 106           Mainline Prot            $50-75k 1107
    ## 107           Mainline Prot           $75-100k  939
    ## 108           Mainline Prot          $100-150k  753
    ## 109           Mainline Prot              >150k  634
    ## 110           Mainline Prot Don't know/refused 1328
    ## 111                  Mormon              <$10k   29
    ## 112                  Mormon            $10-20k   40
    ## 113                  Mormon            $20-30k   48
    ## 114                  Mormon            $30-40k   51
    ## 115                  Mormon            $40-50k   56
    ## 116                  Mormon            $50-75k  112
    ## 117                  Mormon           $75-100k   85
    ## 118                  Mormon          $100-150k   49
    ## 119                  Mormon              >150k   42
    ## 120                  Mormon Don't know/refused   69
    ## 121                  Muslim              <$10k    6
    ## 122                  Muslim            $10-20k    7
    ## 123                  Muslim            $20-30k    9
    ## 124                  Muslim            $30-40k   10
    ## 125                  Muslim            $40-50k    9
    ## 126                  Muslim            $50-75k   23
    ## 127                  Muslim           $75-100k   16
    ## 128                  Muslim          $100-150k    8
    ## 129                  Muslim              >150k    6
    ## 130                  Muslim Don't know/refused   22
    ## 131                Orthodox              <$10k   13
    ## 132                Orthodox            $10-20k   17
    ## 133                Orthodox            $20-30k   23
    ## 134                Orthodox            $30-40k   32
    ## 135                Orthodox            $40-50k   32
    ## 136                Orthodox            $50-75k   47
    ## 137                Orthodox           $75-100k   38
    ## 138                Orthodox          $100-150k   42
    ## 139                Orthodox              >150k   46
    ## 140                Orthodox Don't know/refused   73
    ## 141         Other Christian              <$10k    9
    ## 142         Other Christian            $10-20k    7
    ## 143         Other Christian            $20-30k   11
    ## 144         Other Christian            $30-40k   13
    ## 145         Other Christian            $40-50k   13
    ## 146         Other Christian            $50-75k   14
    ## 147         Other Christian           $75-100k   18
    ## 148         Other Christian          $100-150k   14
    ## 149         Other Christian              >150k   12
    ## 150         Other Christian Don't know/refused   18
    ## 151            Other Faiths              <$10k   20
    ## 152            Other Faiths            $10-20k   33
    ## 153            Other Faiths            $20-30k   40
    ## 154            Other Faiths            $30-40k   46
    ## 155            Other Faiths            $40-50k   49
    ## 156            Other Faiths            $50-75k   63
    ## 157            Other Faiths           $75-100k   46
    ## 158            Other Faiths          $100-150k   40
    ## 159            Other Faiths              >150k   41
    ## 160            Other Faiths Don't know/refused   71
    ## 161   Other World Religions              <$10k    5
    ## 162   Other World Religions            $10-20k    2
    ## 163   Other World Religions            $20-30k    3
    ## 164   Other World Religions            $30-40k    4
    ## 165   Other World Religions            $40-50k    2
    ## 166   Other World Religions            $50-75k    7
    ## 167   Other World Religions           $75-100k    3
    ## 168   Other World Religions          $100-150k    4
    ## 169   Other World Religions              >150k    4
    ## 170   Other World Religions Don't know/refused    8
    ## 171            Unaffiliated              <$10k  217
    ## 172            Unaffiliated            $10-20k  299
    ## 173            Unaffiliated            $20-30k  374
    ## 174            Unaffiliated            $30-40k  365
    ## 175            Unaffiliated            $40-50k  341
    ## 176            Unaffiliated            $50-75k  528
    ## 177            Unaffiliated           $75-100k  407
    ## 178            Unaffiliated          $100-150k  321
    ## 179            Unaffiliated              >150k  258
    ## 180            Unaffiliated Don't know/refused  597
