Laboratorio
================
Mafer Pérez
31 de julio de 2019

``` r
files <- list.files(path="lab", full.names = T)
list(files)
```

    ## [[1]]
    ##  [1] "lab/01-2018.xlsx" "lab/02-2018.xlsx" "lab/03-2018.xlsx"
    ##  [4] "lab/04-2018.xlsx" "lab/05-2018.xlsx" "lab/06-2018.xlsx"
    ##  [7] "lab/07-2018.xlsx" "lab/08-2018.xlsx" "lab/09-2018.xlsx"
    ## [10] "lab/10-2018.xlsx" "lab/11-2018.xlsx"

``` r
library(openxlsx)
```

    ## Warning: package 'openxlsx' was built under R version 3.5.3

``` r
lab1 <- lapply(files, function(filename){
  print(paste("Merging",sep =" "))
  df <- readWorkbook(filename)
  df$mes <- substr(filename,5,6)
  df$anio <- 2018
  return(df[c('COD_VIAJE','CLIENTE','UBICACION','CANTIDAD','PILOTO','Q', 'CREDITO','UNIDAD', 'mes', 'anio')])
})
```

    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"
    ## [1] "Merging"

``` r
lab1
```

    ## [[1]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10000001            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 2    10000002                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 3    10000003           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 4    10000004                                TAQUERIA EL CHINITO     76002
    ## 5    10000005      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 6    10000006                            UBIQUO LABS |||FALTANTE     76001
    ## 7    10000007      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 8    10000008                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 9    10000009                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 10   10000010      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 11   10000011                EL GALLO NEGRO / Despacho a cliente     76001
    ## 12   10000012 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 13   10000013                          POLLO PINULITO|||FALTANTE     76001
    ## 14   10000014                EL GALLO NEGRO / Despacho a cliente     76001
    ## 15   10000015                                TAQUERIA EL CHINITO     76001
    ## 16   10000016            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 17   10000017        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 18   10000018           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 19   10000019           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 20   10000020                                        UBIQUO LABS     76001
    ## 21   10000021           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 22   10000022                                     BAR LA OFICINA     76001
    ## 23   10000023                            UBIQUO LABS |||FALTANTE     76001
    ## 24   10000024           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 25   10000025           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 26   10000026      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 27   10000027            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 28   10000028        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 29   10000029           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 30   10000030                                TAQUERIA EL CHINITO     76002
    ## 31   10000031            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 32   10000032                                TAQUERIA EL CHINITO     76002
    ## 33   10000033                     EL PINCHE OBELISCO |||Faltante     76002
    ## 34   10000034                                        UBIQUO LABS     76001
    ## 35   10000035 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 36   10000036                            UBIQUO LABS |||FALTANTE     76002
    ## 37   10000037                     EL PINCHE OBELISCO |||Faltante     76001
    ## 38   10000038        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 39   10000039            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 40   10000040                                TAQUERIA EL CHINITO     76001
    ## 41   10000041 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 42   10000042                            UBIQUO LABS |||FALTANTE     76002
    ## 43   10000043           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 44   10000044            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 45   10000045           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 46   10000046           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 47   10000047                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 48   10000048        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 49   10000049                  POLLO PINULITO/Despacho a cliente     76002
    ## 50   10000050           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 51   10000051                              HOSPITAL LAS AMERICAS     76001
    ## 52   10000052                                     BAR LA OFICINA     76002
    ## 53   10000053                EL GALLO NEGRO / Despacho a cliente     76001
    ## 54   10000054            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 55   10000055                  POLLO PINULITO/Despacho a cliente     76002
    ## 56   10000056                                     BAR LA OFICINA     76002
    ## 57   10000057                     EL PINCHE OBELISCO |||Faltante     76002
    ## 58   10000058                                        UBIQUO LABS     76001
    ## 59   10000059           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 60   10000060                                     BAR LA OFICINA     76002
    ## 61   10000061                                     BAR LA OFICINA     76002
    ## 62   10000062                                TAQUERIA EL CHINITO     76001
    ## 63   10000063 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 64   10000064                          POLLO PINULITO|||FALTANTE     76002
    ## 65   10000065                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 66   10000066                                     BAR LA OFICINA     76001
    ## 67   10000067                                        UBIQUO LABS     76002
    ## 68   10000068                                TAQUERIA EL CHINITO     76002
    ## 69   10000069                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 70   10000070                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 71   10000071                     EL PINCHE OBELISCO |||Faltante     76002
    ## 72   10000072                                     BAR LA OFICINA     76002
    ## 73   10000073                     EL PINCHE OBELISCO |||Faltante     76002
    ## 74   10000074                     EL PINCHE OBELISCO |||Faltante     76001
    ## 75   10000075                                     BAR LA OFICINA     76001
    ## 76   10000076                EL GALLO NEGRO / Despacho a cliente     76002
    ## 77   10000077            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 78   10000078        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 79   10000079 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 80   10000080                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 81   10000081           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 82   10000082 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 83   10000083           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 84   10000084            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 85   10000085           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 86   10000086                     EL PINCHE OBELISCO |||Faltante     76001
    ## 87   10000087 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 88   10000088                EL GALLO NEGRO / Despacho a cliente     76001
    ## 89   10000089            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 90   10000090                          POLLO PINULITO|||FALTANTE     76002
    ## 91   10000091 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 92   10000092        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 93   10000093                                     BAR LA OFICINA     76002
    ## 94   10000094                  POLLO PINULITO/Despacho a cliente     76002
    ## 95   10000095           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 96   10000096      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 97   10000097                                        UBIQUO LABS     76001
    ## 98   10000098                  POLLO PINULITO/Despacho a cliente     76002
    ## 99   10000099                     EL PINCHE OBELISCO |||Faltante     76001
    ## 100  10000100                                     BAR LA OFICINA     76001
    ## 101  10000101                     EL PINCHE OBELISCO |||Faltante     76001
    ## 102  10000102                          POLLO PINULITO|||FALTANTE     76001
    ## 103  10000103                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 104  10000104            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 105  10000105                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 106  10000106        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 107  10000107 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 108  10000108 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 109  10000109                                        UBIQUO LABS     76001
    ## 110  10000110                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 111  10000111      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 112  10000112            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 113  10000113                                TAQUERIA EL CHINITO     76001
    ## 114  10000114           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 115  10000115                              HOSPITAL LAS AMERICAS     76001
    ## 116  10000116                EL GALLO NEGRO / Despacho a cliente     76001
    ## 117  10000117           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 118  10000118            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 119  10000119           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 120  10000120                                TAQUERIA EL CHINITO     76002
    ## 121  10000121                                        UBIQUO LABS     76001
    ## 122  10000122                     EL PINCHE OBELISCO |||Faltante     76001
    ## 123  10000123 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 124  10000124                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 125  10000125                          POLLO PINULITO|||FALTANTE     76002
    ## 126  10000126                  POLLO PINULITO/Despacho a cliente     76002
    ## 127  10000127                                TAQUERIA EL CHINITO     76001
    ## 128  10000128                  POLLO PINULITO/Despacho a cliente     76001
    ## 129  10000129            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 130  10000130 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 131  10000131                                     BAR LA OFICINA     76002
    ## 132  10000132                     EL PINCHE OBELISCO |||Faltante     76002
    ## 133  10000133                          POLLO PINULITO|||FALTANTE     76002
    ## 134  10000134 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 135  10000135                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 136  10000136                     EL PINCHE OBELISCO |||Faltante     76001
    ## 137  10000137           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 138  10000138                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 139  10000139            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 140  10000140                                     BAR LA OFICINA     76001
    ## 141  10000141                     EL PINCHE OBELISCO |||Faltante     76002
    ## 142  10000142        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 143  10000143        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 144  10000144        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 145  10000145 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 146  10000146                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 147  10000147                     EL PINCHE OBELISCO |||Faltante     76001
    ## 148  10000148                                        UBIQUO LABS     76001
    ## 149  10000149                                TAQUERIA EL CHINITO     76001
    ## 150  10000150            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 151  10000151      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 152  10000152                                TAQUERIA EL CHINITO     76001
    ## 153  10000153        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 154  10000154 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 155  10000155                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 156  10000156            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 157  10000157                  POLLO PINULITO/Despacho a cliente     76001
    ## 158  10000158                     EL PINCHE OBELISCO |||Faltante     76001
    ## 159  10000159                                     BAR LA OFICINA     76001
    ## 160  10000160            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 161  10000161        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 162  10000162                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 163  10000163            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 164  10000164                EL GALLO NEGRO / Despacho a cliente     76002
    ## 165  10000165                                TAQUERIA EL CHINITO     76001
    ## 166  10000166                                     BAR LA OFICINA     76001
    ## 167  10000167        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 168  10000168                     EL PINCHE OBELISCO |||Faltante     76001
    ## 169  10000169 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 170  10000170                            UBIQUO LABS |||FALTANTE     76001
    ## 171  10000171                  POLLO PINULITO/Despacho a cliente     76001
    ## 172  10000172                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 173  10000173        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 174  10000174                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 175  10000175                                TAQUERIA EL CHINITO     76002
    ## 176  10000176                                TAQUERIA EL CHINITO     76002
    ## 177  10000177                            UBIQUO LABS |||FALTANTE     76002
    ## 178  10000178        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 179  10000179                                TAQUERIA EL CHINITO     76002
    ## 180  10000180                                TAQUERIA EL CHINITO     76002
    ## 181  10000181                          POLLO PINULITO|||FALTANTE     76002
    ## 182  10000182            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 183  10000183           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 184  10000184                                     BAR LA OFICINA     76002
    ## 185  10000185           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 186  10000186                                        UBIQUO LABS     76002
    ## 187  10000187                                        UBIQUO LABS     76001
    ## 188  10000188           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 189  10000189                                TAQUERIA EL CHINITO     76001
    ## 190  10000190        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 191  10000191                                TAQUERIA EL CHINITO     76002
    ## 192  10000192            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1200       Fernando Mariano Berrio 300.00      30  Camion Grande
    ## 2       1433        Hector Aragones Frutos 358.25      90  Camion Grande
    ## 3       1857          Pedro Alvarez Parejo 464.25      60  Camion Grande
    ## 4        339          Angel Valdez Alegria  84.75      30          Panel
    ## 5       1644 Juan Francisco Portillo Gomez 411.00      30  Camion Grande
    ## 6       1827             Luis Jaime Urbano 456.75      30  Camion Grande
    ## 7       1947      Ismael Rodero Monteagudo 486.75      90  Camion Grande
    ## 8       1716 Juan Francisco Portillo Gomez 429.00      60  Camion Grande
    ## 9       1601      Ismael Rodero Monteagudo 400.25      30  Camion Grande
    ## 10      1343       Fernando Mariano Berrio 335.75      90  Camion Grande
    ## 11      1782             Luis Jaime Urbano 445.50      60  Camion Grande
    ## 12       234              Felipe Villatoro  58.50      30          Panel
    ## 13      1542        Hector Aragones Frutos 385.50      60  Camion Grande
    ## 14       304        Hector Aragones Frutos  76.00      90          Panel
    ## 15      1667             Luis Jaime Urbano 416.75      90  Camion Grande
    ## 16      1325             Luis Jaime Urbano 331.25      30  Camion Grande
    ## 17      1186      Ismael Rodero Monteagudo 296.50      30  Camion Grande
    ## 18       231      Ismael Rodero Monteagudo  57.75      60          Panel
    ## 19       783          Pedro Alvarez Parejo 195.75      30 Camion Pequeño
    ## 20       971              Felipe Villatoro 242.75      60 Camion Pequeño
    ## 21       547       Fernando Mariano Berrio 136.75      90 Camion Pequeño
    ## 22      1550       Fernando Mariano Berrio 387.50      30  Camion Grande
    ## 23       335          Pedro Alvarez Parejo  83.75      60          Panel
    ## 24      1173          Pedro Alvarez Parejo 293.25      90  Camion Grande
    ## 25      1061       Fernando Mariano Berrio 265.25      60  Camion Grande
    ## 26       840 Juan Francisco Portillo Gomez 210.00      30 Camion Pequeño
    ## 27       795       Fernando Mariano Berrio 198.75      60 Camion Pequeño
    ## 28      1330          Angel Valdez Alegria 332.50      30  Camion Grande
    ## 29      1648 Juan Francisco Portillo Gomez 412.00      30  Camion Grande
    ## 30      1502                  Hector Giron 375.50      90  Camion Grande
    ## 31      1659 Juan Francisco Portillo Gomez 414.75      30  Camion Grande
    ## 32      1508                  Hector Giron 377.00      60  Camion Grande
    ## 33       875 Juan Francisco Portillo Gomez 218.75      60 Camion Pequeño
    ## 34       342        Hector Aragones Frutos  85.50      60          Panel
    ## 35      1980          Pedro Alvarez Parejo 495.00      60  Camion Grande
    ## 36      1442              Felipe Villatoro 360.50      30  Camion Grande
    ## 37      1467        Hector Aragones Frutos 366.75      60  Camion Grande
    ## 38      1991        Hector Aragones Frutos 497.75      90  Camion Grande
    ## 39      1589        Hector Aragones Frutos 397.25      30  Camion Grande
    ## 40       732              Felipe Villatoro 183.00      30 Camion Pequeño
    ## 41       766              Felipe Villatoro 191.50      30 Camion Pequeño
    ## 42       827        Hector Aragones Frutos 206.75      90 Camion Pequeño
    ## 43      1027       Fernando Mariano Berrio 256.75      60  Camion Grande
    ## 44      1706             Luis Jaime Urbano 426.50      60  Camion Grande
    ## 45      1044      Ismael Rodero Monteagudo 261.00      60  Camion Grande
    ## 46       596             Luis Jaime Urbano 149.00      60 Camion Pequeño
    ## 47       362             Luis Jaime Urbano  90.50      90          Panel
    ## 48      1937      Ismael Rodero Monteagudo 484.25      60  Camion Grande
    ## 49       297          Angel Valdez Alegria  74.25      90          Panel
    ## 50       400      Ismael Rodero Monteagudo 100.00      90          Panel
    ## 51       225        Hector Aragones Frutos  56.25      60          Panel
    ## 52       562      Ismael Rodero Monteagudo 140.50      60 Camion Pequeño
    ## 53      1791       Fernando Mariano Berrio 447.75      60  Camion Grande
    ## 54       356             Luis Jaime Urbano  89.00      30          Panel
    ## 55      1903             Luis Jaime Urbano 475.75      30  Camion Grande
    ## 56      1231          Pedro Alvarez Parejo 307.75      30  Camion Grande
    ## 57      1682        Hector Aragones Frutos 420.50      60  Camion Grande
    ## 58      1653          Pedro Alvarez Parejo 413.25      90  Camion Grande
    ## 59      1907          Angel Valdez Alegria 476.75      30  Camion Grande
    ## 60      1954      Ismael Rodero Monteagudo 488.50      90  Camion Grande
    ## 61      1177          Pedro Alvarez Parejo 294.25      90  Camion Grande
    ## 62      1247 Juan Francisco Portillo Gomez 311.75      90  Camion Grande
    ## 63      1551                  Hector Giron 387.75      90  Camion Grande
    ## 64      1481             Luis Jaime Urbano 370.25      30  Camion Grande
    ## 65      1126          Angel Valdez Alegria 281.50      60  Camion Grande
    ## 66      1239             Luis Jaime Urbano 309.75      30  Camion Grande
    ## 67      1598       Fernando Mariano Berrio 399.50      90  Camion Grande
    ## 68       965                  Hector Giron 241.25      90 Camion Pequeño
    ## 69      1111        Hector Aragones Frutos 277.75      30  Camion Grande
    ## 70      1092          Pedro Alvarez Parejo 273.00      30  Camion Grande
    ## 71      1107      Ismael Rodero Monteagudo 276.75      30  Camion Grande
    ## 72       958      Ismael Rodero Monteagudo 239.50      90 Camion Pequeño
    ## 73      1402              Felipe Villatoro 350.50      60  Camion Grande
    ## 74      1059 Juan Francisco Portillo Gomez 264.75      60  Camion Grande
    ## 75       592              Felipe Villatoro 148.00      30 Camion Pequeño
    ## 76      1278             Luis Jaime Urbano 319.50      90  Camion Grande
    ## 77      1578                  Hector Giron 394.50      90  Camion Grande
    ## 78      1760 Juan Francisco Portillo Gomez 440.00      30  Camion Grande
    ## 79       628          Angel Valdez Alegria 157.00      90 Camion Pequeño
    ## 80      1221          Angel Valdez Alegria 305.25      60  Camion Grande
    ## 81       547       Fernando Mariano Berrio 136.75      30 Camion Pequeño
    ## 82       742       Fernando Mariano Berrio 185.50      30 Camion Pequeño
    ## 83      1709          Pedro Alvarez Parejo 427.25      90  Camion Grande
    ## 84      1769          Pedro Alvarez Parejo 442.25      30  Camion Grande
    ## 85       384      Ismael Rodero Monteagudo  96.00      90          Panel
    ## 86      1203      Ismael Rodero Monteagudo 300.75      60  Camion Grande
    ## 87       663                  Hector Giron 165.75      90 Camion Pequeño
    ## 88       929                  Hector Giron 232.25      90 Camion Pequeño
    ## 89       859        Hector Aragones Frutos 214.75      60 Camion Pequeño
    ## 90      1144          Pedro Alvarez Parejo 286.00      60  Camion Grande
    ## 91      1351        Hector Aragones Frutos 337.75      90  Camion Grande
    ## 92      1134 Juan Francisco Portillo Gomez 283.50      30  Camion Grande
    ## 93      1929          Pedro Alvarez Parejo 482.25      90  Camion Grande
    ## 94      1285              Felipe Villatoro 321.25      30  Camion Grande
    ## 95      1256          Angel Valdez Alegria 314.00      30  Camion Grande
    ## 96       516        Hector Aragones Frutos 129.00      30 Camion Pequeño
    ## 97       829          Angel Valdez Alegria 207.25      30 Camion Pequeño
    ## 98      1706       Fernando Mariano Berrio 426.50      90  Camion Grande
    ## 99      1201      Ismael Rodero Monteagudo 300.25      60  Camion Grande
    ## 100     1373      Ismael Rodero Monteagudo 343.25      30  Camion Grande
    ## 101     1164       Fernando Mariano Berrio 291.00      90  Camion Grande
    ## 102     1405             Luis Jaime Urbano 351.25      60  Camion Grande
    ## 103     1722          Pedro Alvarez Parejo 430.50      30  Camion Grande
    ## 104      666          Pedro Alvarez Parejo 166.50      90 Camion Pequeño
    ## 105      595      Ismael Rodero Monteagudo 148.75      60 Camion Pequeño
    ## 106      482              Felipe Villatoro 120.50      90          Panel
    ## 107     1340       Fernando Mariano Berrio 335.00      90  Camion Grande
    ## 108     1887          Pedro Alvarez Parejo 471.75      60  Camion Grande
    ## 109      835                  Hector Giron 208.75      30 Camion Pequeño
    ## 110      696             Luis Jaime Urbano 174.00      60 Camion Pequeño
    ## 111      414       Fernando Mariano Berrio 103.50      60          Panel
    ## 112     1888          Pedro Alvarez Parejo 472.00      30  Camion Grande
    ## 113     1080              Felipe Villatoro 270.00      30  Camion Grande
    ## 114     1070 Juan Francisco Portillo Gomez 267.50      90  Camion Grande
    ## 115      710       Fernando Mariano Berrio 177.50      60 Camion Pequeño
    ## 116      557              Felipe Villatoro 139.25      90 Camion Pequeño
    ## 117     1666      Ismael Rodero Monteagudo 416.50      90  Camion Grande
    ## 118     1456                  Hector Giron 364.00      30  Camion Grande
    ## 119     1652                  Hector Giron 413.00      60  Camion Grande
    ## 120     1153        Hector Aragones Frutos 288.25      90  Camion Grande
    ## 121     1668                  Hector Giron 417.00      60  Camion Grande
    ## 122     1315       Fernando Mariano Berrio 328.75      90  Camion Grande
    ## 123     1695 Juan Francisco Portillo Gomez 423.75      90  Camion Grande
    ## 124     1618              Felipe Villatoro 404.50      30  Camion Grande
    ## 125     1912          Angel Valdez Alegria 478.00      30  Camion Grande
    ## 126     1112              Felipe Villatoro 278.00      90  Camion Grande
    ## 127      828              Felipe Villatoro 207.00      90 Camion Pequeño
    ## 128     1820          Pedro Alvarez Parejo 455.00      30  Camion Grande
    ## 129      306          Pedro Alvarez Parejo  76.50      90          Panel
    ## 130     1459        Hector Aragones Frutos 364.75      30  Camion Grande
    ## 131     1230          Angel Valdez Alegria 307.50      90  Camion Grande
    ## 132      456 Juan Francisco Portillo Gomez 114.00      30          Panel
    ## 133      248          Pedro Alvarez Parejo  62.00      30          Panel
    ## 134      237       Fernando Mariano Berrio  59.25      30          Panel
    ## 135     1280       Fernando Mariano Berrio 320.00      60  Camion Grande
    ## 136     1193              Felipe Villatoro 298.25      30  Camion Grande
    ## 137     1294                  Hector Giron 323.50      90  Camion Grande
    ## 138     1435          Pedro Alvarez Parejo 358.75      90  Camion Grande
    ## 139     1589        Hector Aragones Frutos 397.25      30  Camion Grande
    ## 140     1259          Angel Valdez Alegria 314.75      90  Camion Grande
    ## 141     1544      Ismael Rodero Monteagudo 386.00      60  Camion Grande
    ## 142      894 Juan Francisco Portillo Gomez 223.50      60 Camion Pequeño
    ## 143     1764                  Hector Giron 441.00      90  Camion Grande
    ## 144      540          Angel Valdez Alegria 135.00      30 Camion Pequeño
    ## 145     1383              Felipe Villatoro 345.75      60  Camion Grande
    ## 146      288             Luis Jaime Urbano  72.00      60          Panel
    ## 147      636        Hector Aragones Frutos 159.00      90 Camion Pequeño
    ## 148      311          Angel Valdez Alegria  77.75      60          Panel
    ## 149      936       Fernando Mariano Berrio 234.00      90 Camion Pequeño
    ## 150     1607       Fernando Mariano Berrio 401.75      30  Camion Grande
    ## 151     1459                  Hector Giron 364.75      60  Camion Grande
    ## 152      743             Luis Jaime Urbano 185.75      60 Camion Pequeño
    ## 153     1952                  Hector Giron 488.00      30  Camion Grande
    ## 154     1575              Felipe Villatoro 393.75      30  Camion Grande
    ## 155      344          Pedro Alvarez Parejo  86.00      90          Panel
    ## 156      215          Angel Valdez Alegria  53.75      60          Panel
    ## 157     1685 Juan Francisco Portillo Gomez 421.25      90  Camion Grande
    ## 158     1904          Angel Valdez Alegria 476.00      30  Camion Grande
    ## 159      974                  Hector Giron 243.50      30 Camion Pequeño
    ## 160      369              Felipe Villatoro  92.25      30          Panel
    ## 161      609      Ismael Rodero Monteagudo 152.25      90 Camion Pequeño
    ## 162      209       Fernando Mariano Berrio  52.25      60          Panel
    ## 163     1814      Ismael Rodero Monteagudo 453.50      60  Camion Grande
    ## 164     1729      Ismael Rodero Monteagudo 432.25      30  Camion Grande
    ## 165      349        Hector Aragones Frutos  87.25      60          Panel
    ## 166      890             Luis Jaime Urbano 222.50      30 Camion Pequeño
    ## 167      557       Fernando Mariano Berrio 139.25      60 Camion Pequeño
    ## 168      726             Luis Jaime Urbano 181.50      90 Camion Pequeño
    ## 169     1545 Juan Francisco Portillo Gomez 386.25      30  Camion Grande
    ## 170      596          Pedro Alvarez Parejo 149.00      90 Camion Pequeño
    ## 171     1232             Luis Jaime Urbano 308.00      60  Camion Grande
    ## 172     1442       Fernando Mariano Berrio 360.50      30  Camion Grande
    ## 173     1245          Angel Valdez Alegria 311.25      30  Camion Grande
    ## 174     1398          Angel Valdez Alegria 349.50      60  Camion Grande
    ## 175     1305 Juan Francisco Portillo Gomez 326.25      30  Camion Grande
    ## 176      630              Felipe Villatoro 157.50      60 Camion Pequeño
    ## 177     1047             Luis Jaime Urbano 261.75      30  Camion Grande
    ## 178     1235          Angel Valdez Alegria 308.75      60  Camion Grande
    ## 179     1271              Felipe Villatoro 317.75      60  Camion Grande
    ## 180      862          Pedro Alvarez Parejo 215.50      30 Camion Pequeño
    ## 181     1345 Juan Francisco Portillo Gomez 336.25      60  Camion Grande
    ## 182     1044          Angel Valdez Alegria 261.00      30  Camion Grande
    ## 183     1876 Juan Francisco Portillo Gomez 469.00      60  Camion Grande
    ## 184      898      Ismael Rodero Monteagudo 224.50      60 Camion Pequeño
    ## 185     1398        Hector Aragones Frutos 349.50      30  Camion Grande
    ## 186     1719          Pedro Alvarez Parejo 429.75      30  Camion Grande
    ## 187     1847          Angel Valdez Alegria 461.75      30  Camion Grande
    ## 188      407          Pedro Alvarez Parejo 101.75      90          Panel
    ## 189     1699       Fernando Mariano Berrio 424.75      90  Camion Grande
    ## 190     1061                  Hector Giron 265.25      90  Camion Grande
    ## 191     1447                  Hector Giron 361.75      60  Camion Grande
    ## 192      496      Ismael Rodero Monteagudo 124.00      90          Panel
    ##     mes anio
    ## 1    01 2018
    ## 2    01 2018
    ## 3    01 2018
    ## 4    01 2018
    ## 5    01 2018
    ## 6    01 2018
    ## 7    01 2018
    ## 8    01 2018
    ## 9    01 2018
    ## 10   01 2018
    ## 11   01 2018
    ## 12   01 2018
    ## 13   01 2018
    ## 14   01 2018
    ## 15   01 2018
    ## 16   01 2018
    ## 17   01 2018
    ## 18   01 2018
    ## 19   01 2018
    ## 20   01 2018
    ## 21   01 2018
    ## 22   01 2018
    ## 23   01 2018
    ## 24   01 2018
    ## 25   01 2018
    ## 26   01 2018
    ## 27   01 2018
    ## 28   01 2018
    ## 29   01 2018
    ## 30   01 2018
    ## 31   01 2018
    ## 32   01 2018
    ## 33   01 2018
    ## 34   01 2018
    ## 35   01 2018
    ## 36   01 2018
    ## 37   01 2018
    ## 38   01 2018
    ## 39   01 2018
    ## 40   01 2018
    ## 41   01 2018
    ## 42   01 2018
    ## 43   01 2018
    ## 44   01 2018
    ## 45   01 2018
    ## 46   01 2018
    ## 47   01 2018
    ## 48   01 2018
    ## 49   01 2018
    ## 50   01 2018
    ## 51   01 2018
    ## 52   01 2018
    ## 53   01 2018
    ## 54   01 2018
    ## 55   01 2018
    ## 56   01 2018
    ## 57   01 2018
    ## 58   01 2018
    ## 59   01 2018
    ## 60   01 2018
    ## 61   01 2018
    ## 62   01 2018
    ## 63   01 2018
    ## 64   01 2018
    ## 65   01 2018
    ## 66   01 2018
    ## 67   01 2018
    ## 68   01 2018
    ## 69   01 2018
    ## 70   01 2018
    ## 71   01 2018
    ## 72   01 2018
    ## 73   01 2018
    ## 74   01 2018
    ## 75   01 2018
    ## 76   01 2018
    ## 77   01 2018
    ## 78   01 2018
    ## 79   01 2018
    ## 80   01 2018
    ## 81   01 2018
    ## 82   01 2018
    ## 83   01 2018
    ## 84   01 2018
    ## 85   01 2018
    ## 86   01 2018
    ## 87   01 2018
    ## 88   01 2018
    ## 89   01 2018
    ## 90   01 2018
    ## 91   01 2018
    ## 92   01 2018
    ## 93   01 2018
    ## 94   01 2018
    ## 95   01 2018
    ## 96   01 2018
    ## 97   01 2018
    ## 98   01 2018
    ## 99   01 2018
    ## 100  01 2018
    ## 101  01 2018
    ## 102  01 2018
    ## 103  01 2018
    ## 104  01 2018
    ## 105  01 2018
    ## 106  01 2018
    ## 107  01 2018
    ## 108  01 2018
    ## 109  01 2018
    ## 110  01 2018
    ## 111  01 2018
    ## 112  01 2018
    ## 113  01 2018
    ## 114  01 2018
    ## 115  01 2018
    ## 116  01 2018
    ## 117  01 2018
    ## 118  01 2018
    ## 119  01 2018
    ## 120  01 2018
    ## 121  01 2018
    ## 122  01 2018
    ## 123  01 2018
    ## 124  01 2018
    ## 125  01 2018
    ## 126  01 2018
    ## 127  01 2018
    ## 128  01 2018
    ## 129  01 2018
    ## 130  01 2018
    ## 131  01 2018
    ## 132  01 2018
    ## 133  01 2018
    ## 134  01 2018
    ## 135  01 2018
    ## 136  01 2018
    ## 137  01 2018
    ## 138  01 2018
    ## 139  01 2018
    ## 140  01 2018
    ## 141  01 2018
    ## 142  01 2018
    ## 143  01 2018
    ## 144  01 2018
    ## 145  01 2018
    ## 146  01 2018
    ## 147  01 2018
    ## 148  01 2018
    ## 149  01 2018
    ## 150  01 2018
    ## 151  01 2018
    ## 152  01 2018
    ## 153  01 2018
    ## 154  01 2018
    ## 155  01 2018
    ## 156  01 2018
    ## 157  01 2018
    ## 158  01 2018
    ## 159  01 2018
    ## 160  01 2018
    ## 161  01 2018
    ## 162  01 2018
    ## 163  01 2018
    ## 164  01 2018
    ## 165  01 2018
    ## 166  01 2018
    ## 167  01 2018
    ## 168  01 2018
    ## 169  01 2018
    ## 170  01 2018
    ## 171  01 2018
    ## 172  01 2018
    ## 173  01 2018
    ## 174  01 2018
    ## 175  01 2018
    ## 176  01 2018
    ## 177  01 2018
    ## 178  01 2018
    ## 179  01 2018
    ## 180  01 2018
    ## 181  01 2018
    ## 182  01 2018
    ## 183  01 2018
    ## 184  01 2018
    ## 185  01 2018
    ## 186  01 2018
    ## 187  01 2018
    ## 188  01 2018
    ## 189  01 2018
    ## 190  01 2018
    ## 191  01 2018
    ## 192  01 2018
    ## 
    ## [[2]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10000193        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 2    10000194                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 3    10000195                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 4    10000196           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 5    10000197                          POLLO PINULITO|||FALTANTE     76002
    ## 6    10000198                          POLLO PINULITO|||FALTANTE     76002
    ## 7    10000199                                TAQUERIA EL CHINITO     76001
    ## 8    10000200                     EL PINCHE OBELISCO |||Faltante     76001
    ## 9    10000201                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 10   10000202           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 11   10000203                     EL PINCHE OBELISCO |||Faltante     76002
    ## 12   10000204                  POLLO PINULITO/Despacho a cliente     76001
    ## 13   10000205            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 14   10000206        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 15   10000207                  POLLO PINULITO/Despacho a cliente     76002
    ## 16   10000208            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 17   10000209                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 18   10000210            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 19   10000211      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 20   10000212      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 21   10000213           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 22   10000214                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 23   10000215           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 24   10000216                                TAQUERIA EL CHINITO     76001
    ## 25   10000217           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 26   10000218                          POLLO PINULITO|||FALTANTE     76001
    ## 27   10000219                                        UBIQUO LABS     76002
    ## 28   10000220                                     BAR LA OFICINA     76002
    ## 29   10000221                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 30   10000222                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 31   10000223      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 32   10000224                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 33   10000225 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 34   10000226            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 35   10000227                EL GALLO NEGRO / Despacho a cliente     76001
    ## 36   10000228           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 37   10000229                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 38   10000230           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 39   10000231                                     BAR LA OFICINA     76001
    ## 40   10000232            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 41   10000233                                        UBIQUO LABS     76001
    ## 42   10000234            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 43   10000235        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 44   10000236                                     BAR LA OFICINA     76001
    ## 45   10000237           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 46   10000238                                        UBIQUO LABS     76002
    ## 47   10000239        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 48   10000240                     EL PINCHE OBELISCO |||Faltante     76001
    ## 49   10000241                                     BAR LA OFICINA     76001
    ## 50   10000242                                TAQUERIA EL CHINITO     76001
    ## 51   10000243            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 52   10000244                EL GALLO NEGRO / Despacho a cliente     76001
    ## 53   10000245                                TAQUERIA EL CHINITO     76001
    ## 54   10000246                            UBIQUO LABS |||FALTANTE     76002
    ## 55   10000247           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 56   10000248            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 57   10000249      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 58   10000250                          POLLO PINULITO|||FALTANTE     76001
    ## 59   10000251                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 60   10000252      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 61   10000253      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 62   10000254 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 63   10000255                          POLLO PINULITO|||FALTANTE     76001
    ## 64   10000256 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 65   10000257                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 66   10000258           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 67   10000259                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 68   10000260                          POLLO PINULITO|||FALTANTE     76001
    ## 69   10000261                                        UBIQUO LABS     76002
    ## 70   10000262            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 71   10000263                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 72   10000264                     EL PINCHE OBELISCO |||Faltante     76001
    ## 73   10000265            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 74   10000266           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 75   10000267           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 76   10000268                            UBIQUO LABS |||FALTANTE     76001
    ## 77   10000269 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 78   10000270 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 79   10000271 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 80   10000272           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 81   10000273                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 82   10000274                EL GALLO NEGRO / Despacho a cliente     76002
    ## 83   10000275                          POLLO PINULITO|||FALTANTE     76001
    ## 84   10000276                                     BAR LA OFICINA     76002
    ## 85   10000277           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 86   10000278      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 87   10000279                EL GALLO NEGRO / Despacho a cliente     76002
    ## 88   10000280                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 89   10000281                                TAQUERIA EL CHINITO     76002
    ## 90   10000282                                        UBIQUO LABS     76002
    ## 91   10000283                  POLLO PINULITO/Despacho a cliente     76001
    ## 92   10000284                                TAQUERIA EL CHINITO     76001
    ## 93   10000285            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 94   10000286        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 95   10000287           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 96   10000288           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 97   10000289            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 98   10000290                                TAQUERIA EL CHINITO     76002
    ## 99   10000291                            UBIQUO LABS |||FALTANTE     76001
    ## 100  10000292      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 101  10000293                          POLLO PINULITO|||FALTANTE     76002
    ## 102  10000294                          POLLO PINULITO|||FALTANTE     76001
    ## 103  10000295                EL GALLO NEGRO / Despacho a cliente     76002
    ## 104  10000296            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 105  10000297                     EL PINCHE OBELISCO |||Faltante     76001
    ## 106  10000298            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 107  10000299            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 108  10000300                EL GALLO NEGRO / Despacho a cliente     76002
    ## 109  10000301        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 110  10000302                  POLLO PINULITO/Despacho a cliente     76001
    ## 111  10000303                                        UBIQUO LABS     76002
    ## 112  10000304                            UBIQUO LABS |||FALTANTE     76001
    ## 113  10000305                            UBIQUO LABS |||FALTANTE     76002
    ## 114  10000306            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 115  10000307            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 116  10000308           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 117  10000309                            UBIQUO LABS |||FALTANTE     76002
    ## 118  10000310      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 119  10000311                EL GALLO NEGRO / Despacho a cliente     76001
    ## 120  10000312                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 121  10000313           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 122  10000314                            UBIQUO LABS |||FALTANTE     76002
    ## 123  10000315                                        UBIQUO LABS     76001
    ## 124  10000316                                TAQUERIA EL CHINITO     76001
    ## 125  10000317                                        UBIQUO LABS     76001
    ## 126  10000318           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 127  10000319           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 128  10000320                              HOSPITAL LAS AMERICAS     76002
    ## 129  10000321                            UBIQUO LABS |||FALTANTE     76002
    ## 130  10000322            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 131  10000323                              HOSPITAL LAS AMERICAS     76002
    ## 132  10000324 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 133  10000325           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 134  10000326            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 135  10000327                              HOSPITAL LAS AMERICAS     76002
    ## 136  10000328                                TAQUERIA EL CHINITO     76002
    ## 137  10000329            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 138  10000330                                        UBIQUO LABS     76002
    ## 139  10000331                                TAQUERIA EL CHINITO     76002
    ## 140  10000332                                     BAR LA OFICINA     76001
    ## 141  10000333                            UBIQUO LABS |||FALTANTE     76001
    ## 142  10000334            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 143  10000335           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 144  10000336                                     BAR LA OFICINA     76001
    ## 145  10000337                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 146  10000338                  POLLO PINULITO/Despacho a cliente     76002
    ## 147  10000339                                TAQUERIA EL CHINITO     76002
    ## 148  10000340      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 149  10000341                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 150  10000342                              HOSPITAL LAS AMERICAS     76002
    ## 151  10000343            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 152  10000344                     EL PINCHE OBELISCO |||Faltante     76002
    ## 153  10000345                  POLLO PINULITO/Despacho a cliente     76002
    ## 154  10000346                                     BAR LA OFICINA     76002
    ## 155  10000347            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 156  10000348                              HOSPITAL LAS AMERICAS     76001
    ## 157  10000349                          POLLO PINULITO|||FALTANTE     76002
    ## 158  10000350                EL GALLO NEGRO / Despacho a cliente     76002
    ## 159  10000351                  POLLO PINULITO/Despacho a cliente     76001
    ## 160  10000352            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 161  10000353                EL GALLO NEGRO / Despacho a cliente     76001
    ## 162  10000354                                TAQUERIA EL CHINITO     76002
    ## 163  10000355            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 164  10000356 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 165  10000357                EL GALLO NEGRO / Despacho a cliente     76001
    ## 166  10000358                                        UBIQUO LABS     76002
    ## 167  10000359           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 168  10000360            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 169  10000361                                     BAR LA OFICINA     76002
    ## 170  10000362                EL GALLO NEGRO / Despacho a cliente     76002
    ## 171  10000363                              HOSPITAL LAS AMERICAS     76001
    ## 172  10000364                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 173  10000365                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 174  10000366            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 175  10000367                            UBIQUO LABS |||FALTANTE     76002
    ## 176  10000368                            UBIQUO LABS |||FALTANTE     76001
    ## 177  10000369                              HOSPITAL LAS AMERICAS     76001
    ## 178  10000370        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 179  10000371                              HOSPITAL LAS AMERICAS     76002
    ## 180  10000372            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 181  10000373                     EL PINCHE OBELISCO |||Faltante     76002
    ## 182  10000374                                        UBIQUO LABS     76002
    ## 183  10000375           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 184  10000376                                     BAR LA OFICINA     76002
    ## 185  10000377           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 186  10000378                                        UBIQUO LABS     76002
    ## 187  10000379                          POLLO PINULITO|||FALTANTE     76002
    ## 188  10000380                     EL PINCHE OBELISCO |||Faltante     76001
    ## 189  10000381                            UBIQUO LABS |||FALTANTE     76001
    ## 190  10000382           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 191  10000383            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 192  10000384 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 193  10000385            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 194  10000386                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 195  10000387                            UBIQUO LABS |||FALTANTE     76002
    ## 196  10000388 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 197  10000389        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 198  10000390                     EL PINCHE OBELISCO |||Faltante     76001
    ## 199  10000391 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 200  10000392                     EL PINCHE OBELISCO |||Faltante     76001
    ## 201  10000393           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 202  10000394                            UBIQUO LABS |||FALTANTE     76001
    ## 203  10000395      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1        568 Juan Francisco Portillo Gomez 142.00      60 Camion Pequeño
    ## 2        739 Juan Francisco Portillo Gomez 184.75      90 Camion Pequeño
    ## 3        322             Luis Jaime Urbano  80.50      60          Panel
    ## 4        496             Luis Jaime Urbano 124.00      60          Panel
    ## 5       1640        Hector Aragones Frutos 410.00      30  Camion Grande
    ## 6        955          Pedro Alvarez Parejo 238.75      30 Camion Pequeño
    ## 7       1697                  Hector Giron 424.25      90  Camion Grande
    ## 8       1756          Angel Valdez Alegria 439.00      60  Camion Grande
    ## 9       1283          Angel Valdez Alegria 320.75      60  Camion Grande
    ## 10       708              Felipe Villatoro 177.00      30 Camion Pequeño
    ## 11      1509                  Hector Giron 377.25      90  Camion Grande
    ## 12      1333          Angel Valdez Alegria 333.25      90  Camion Grande
    ## 13      1536              Felipe Villatoro 384.00      90  Camion Grande
    ## 14      1062        Hector Aragones Frutos 265.50      30  Camion Grande
    ## 15      1929              Felipe Villatoro 482.25      30  Camion Grande
    ## 16      1698                  Hector Giron 424.50      90  Camion Grande
    ## 17       294          Pedro Alvarez Parejo  73.50      60          Panel
    ## 18       709                  Hector Giron 177.25      60 Camion Pequeño
    ## 19      1817 Juan Francisco Portillo Gomez 454.25      90  Camion Grande
    ## 20      1080       Fernando Mariano Berrio 270.00      60  Camion Grande
    ## 21      1761             Luis Jaime Urbano 440.25      30  Camion Grande
    ## 22      1366             Luis Jaime Urbano 341.50      30  Camion Grande
    ## 23       852          Angel Valdez Alegria 213.00      30 Camion Pequeño
    ## 24      1421       Fernando Mariano Berrio 355.25      30  Camion Grande
    ## 25       919        Hector Aragones Frutos 229.75      30 Camion Pequeño
    ## 26      1163                  Hector Giron 290.75      90  Camion Grande
    ## 27      1775      Ismael Rodero Monteagudo 443.75      90  Camion Grande
    ## 28      1714        Hector Aragones Frutos 428.50      60  Camion Grande
    ## 29      1387          Angel Valdez Alegria 346.75      60  Camion Grande
    ## 30       749              Felipe Villatoro 187.25      30 Camion Pequeño
    ## 31      1763       Fernando Mariano Berrio 440.75      30  Camion Grande
    ## 32      1416             Luis Jaime Urbano 354.00      60  Camion Grande
    ## 33      1471              Felipe Villatoro 367.75      30  Camion Grande
    ## 34      1846          Angel Valdez Alegria 461.50      60  Camion Grande
    ## 35       555          Angel Valdez Alegria 138.75      30 Camion Pequeño
    ## 36      1669              Felipe Villatoro 417.25      60  Camion Grande
    ## 37      1081      Ismael Rodero Monteagudo 270.25      30  Camion Grande
    ## 38       729              Felipe Villatoro 182.25      60 Camion Pequeño
    ## 39      1132          Angel Valdez Alegria 283.00      90  Camion Grande
    ## 40       291       Fernando Mariano Berrio  72.75      30          Panel
    ## 41      1768              Felipe Villatoro 442.00      60  Camion Grande
    ## 42      1798       Fernando Mariano Berrio 449.50      30  Camion Grande
    ## 43       206 Juan Francisco Portillo Gomez  51.50      90          Panel
    ## 44      1295              Felipe Villatoro 323.75      30  Camion Grande
    ## 45       532          Angel Valdez Alegria 133.00      60 Camion Pequeño
    ## 46       732        Hector Aragones Frutos 183.00      90 Camion Pequeño
    ## 47       698          Angel Valdez Alegria 174.50      90 Camion Pequeño
    ## 48      1101        Hector Aragones Frutos 275.25      90  Camion Grande
    ## 49      1155        Hector Aragones Frutos 288.75      60  Camion Grande
    ## 50      1577                  Hector Giron 394.25      30  Camion Grande
    ## 51      1342          Angel Valdez Alegria 335.50      90  Camion Grande
    ## 52      1427             Luis Jaime Urbano 356.75      60  Camion Grande
    ## 53      1490 Juan Francisco Portillo Gomez 372.50      60  Camion Grande
    ## 54       627              Felipe Villatoro 156.75      90 Camion Pequeño
    ## 55      1661 Juan Francisco Portillo Gomez 415.25      60  Camion Grande
    ## 56      1098      Ismael Rodero Monteagudo 274.50      30  Camion Grande
    ## 57      1941          Pedro Alvarez Parejo 485.25      90  Camion Grande
    ## 58      1302          Angel Valdez Alegria 325.50      60  Camion Grande
    ## 59      1498              Felipe Villatoro 374.50      30  Camion Grande
    ## 60       521          Pedro Alvarez Parejo 130.25      90 Camion Pequeño
    ## 61      1714 Juan Francisco Portillo Gomez 428.50      60  Camion Grande
    ## 62       280 Juan Francisco Portillo Gomez  70.00      30          Panel
    ## 63      1867          Angel Valdez Alegria 466.75      30  Camion Grande
    ## 64       347       Fernando Mariano Berrio  86.75      60          Panel
    ## 65       955              Felipe Villatoro 238.75      30 Camion Pequeño
    ## 66      1126              Felipe Villatoro 281.50      90  Camion Grande
    ## 67       225        Hector Aragones Frutos  56.25      30          Panel
    ## 68       479        Hector Aragones Frutos 119.75      60          Panel
    ## 69      1054                  Hector Giron 263.50      30  Camion Grande
    ## 70      1582 Juan Francisco Portillo Gomez 395.50      60  Camion Grande
    ## 71       222      Ismael Rodero Monteagudo  55.50      30          Panel
    ## 72      1307 Juan Francisco Portillo Gomez 326.75      90  Camion Grande
    ## 73       969 Juan Francisco Portillo Gomez 242.25      60 Camion Pequeño
    ## 74      1750          Angel Valdez Alegria 437.50      60  Camion Grande
    ## 75       679                  Hector Giron 169.75      30 Camion Pequeño
    ## 76       788      Ismael Rodero Monteagudo 197.00      30 Camion Pequeño
    ## 77       723 Juan Francisco Portillo Gomez 180.75      60 Camion Pequeño
    ## 78      1913      Ismael Rodero Monteagudo 478.25      60  Camion Grande
    ## 79       665 Juan Francisco Portillo Gomez 166.25      60 Camion Pequeño
    ## 80       930      Ismael Rodero Monteagudo 232.50      30 Camion Pequeño
    ## 81      1003              Felipe Villatoro 250.75      30  Camion Grande
    ## 82       613       Fernando Mariano Berrio 153.25      60 Camion Pequeño
    ## 83       252             Luis Jaime Urbano  63.00      30          Panel
    ## 84      1698       Fernando Mariano Berrio 424.50      90  Camion Grande
    ## 85       956       Fernando Mariano Berrio 239.00      30 Camion Pequeño
    ## 86       830        Hector Aragones Frutos 207.50      60 Camion Pequeño
    ## 87      1071             Luis Jaime Urbano 267.75      90  Camion Grande
    ## 88       602        Hector Aragones Frutos 150.50      30 Camion Pequeño
    ## 89      1890          Angel Valdez Alegria 472.50      60  Camion Grande
    ## 90      1301                  Hector Giron 325.25      90  Camion Grande
    ## 91      1523          Pedro Alvarez Parejo 380.75      60  Camion Grande
    ## 92      1273                  Hector Giron 318.25      90  Camion Grande
    ## 93      1832 Juan Francisco Portillo Gomez 458.00      30  Camion Grande
    ## 94      1956          Pedro Alvarez Parejo 489.00      90  Camion Grande
    ## 95      1026              Felipe Villatoro 256.50      60  Camion Grande
    ## 96      1025             Luis Jaime Urbano 256.25      60  Camion Grande
    ## 97      1526          Pedro Alvarez Parejo 381.50      60  Camion Grande
    ## 98      1361        Hector Aragones Frutos 340.25      90  Camion Grande
    ## 99      1872             Luis Jaime Urbano 468.00      90  Camion Grande
    ## 100      350      Ismael Rodero Monteagudo  87.50      90          Panel
    ## 101     1185             Luis Jaime Urbano 296.25      30  Camion Grande
    ## 102     1568      Ismael Rodero Monteagudo 392.00      30  Camion Grande
    ## 103     1608 Juan Francisco Portillo Gomez 402.00      30  Camion Grande
    ## 104      645             Luis Jaime Urbano 161.25      30 Camion Pequeño
    ## 105      244          Pedro Alvarez Parejo  61.00      60          Panel
    ## 106      615          Angel Valdez Alegria 153.75      60 Camion Pequeño
    ## 107     1897          Pedro Alvarez Parejo 474.25      60  Camion Grande
    ## 108      786             Luis Jaime Urbano 196.50      60 Camion Pequeño
    ## 109      887 Juan Francisco Portillo Gomez 221.75      90 Camion Pequeño
    ## 110     1604              Felipe Villatoro 401.00      90  Camion Grande
    ## 111     1840          Pedro Alvarez Parejo 460.00      30  Camion Grande
    ## 112     1008        Hector Aragones Frutos 252.00      90  Camion Grande
    ## 113     1926 Juan Francisco Portillo Gomez 481.50      30  Camion Grande
    ## 114      737          Pedro Alvarez Parejo 184.25      90 Camion Pequeño
    ## 115     1876       Fernando Mariano Berrio 469.00      60  Camion Grande
    ## 116      336             Luis Jaime Urbano  84.00      60          Panel
    ## 117      489          Pedro Alvarez Parejo 122.25      30          Panel
    ## 118      227 Juan Francisco Portillo Gomez  56.75      60          Panel
    ## 119     1440          Pedro Alvarez Parejo 360.00      30  Camion Grande
    ## 120     1220        Hector Aragones Frutos 305.00      60  Camion Grande
    ## 121     1561      Ismael Rodero Monteagudo 390.25      30  Camion Grande
    ## 122     1988          Pedro Alvarez Parejo 497.00      60  Camion Grande
    ## 123      278        Hector Aragones Frutos  69.50      60          Panel
    ## 124     1227             Luis Jaime Urbano 306.75      60  Camion Grande
    ## 125     1700                  Hector Giron 425.00      60  Camion Grande
    ## 126     1563          Angel Valdez Alegria 390.75      60  Camion Grande
    ## 127      890        Hector Aragones Frutos 222.50      90 Camion Pequeño
    ## 128     1780              Felipe Villatoro 445.00      60  Camion Grande
    ## 129      745                  Hector Giron 186.25      90 Camion Pequeño
    ## 130      906          Pedro Alvarez Parejo 226.50      60 Camion Pequeño
    ## 131      478          Angel Valdez Alegria 119.50      60          Panel
    ## 132     1739      Ismael Rodero Monteagudo 434.75      30  Camion Grande
    ## 133      212          Pedro Alvarez Parejo  53.00      60          Panel
    ## 134     1504 Juan Francisco Portillo Gomez 376.00      30  Camion Grande
    ## 135      789                  Hector Giron 197.25      90 Camion Pequeño
    ## 136     1521      Ismael Rodero Monteagudo 380.25      90  Camion Grande
    ## 137     1282                  Hector Giron 320.50      30  Camion Grande
    ## 138      831 Juan Francisco Portillo Gomez 207.75      30 Camion Pequeño
    ## 139      570             Luis Jaime Urbano 142.50      90 Camion Pequeño
    ## 140      682        Hector Aragones Frutos 170.50      30 Camion Pequeño
    ## 141     1055      Ismael Rodero Monteagudo 263.75      90  Camion Grande
    ## 142      765        Hector Aragones Frutos 191.25      60 Camion Pequeño
    ## 143     1886                  Hector Giron 471.50      30  Camion Grande
    ## 144     1085 Juan Francisco Portillo Gomez 271.25      90  Camion Grande
    ## 145      732             Luis Jaime Urbano 183.00      30 Camion Pequeño
    ## 146      554              Felipe Villatoro 138.50      30 Camion Pequeño
    ## 147      236                  Hector Giron  59.00      60          Panel
    ## 148     1700       Fernando Mariano Berrio 425.00      90  Camion Grande
    ## 149     1460          Angel Valdez Alegria 365.00      30  Camion Grande
    ## 150     1435        Hector Aragones Frutos 358.75      60  Camion Grande
    ## 151     1471       Fernando Mariano Berrio 367.75      30  Camion Grande
    ## 152      761          Pedro Alvarez Parejo 190.25      30 Camion Pequeño
    ## 153     1148          Angel Valdez Alegria 287.00      90  Camion Grande
    ## 154      692                  Hector Giron 173.00      90 Camion Pequeño
    ## 155      253      Ismael Rodero Monteagudo  63.25      90          Panel
    ## 156     1312 Juan Francisco Portillo Gomez 328.00      30  Camion Grande
    ## 157      841          Angel Valdez Alegria 210.25      60 Camion Pequeño
    ## 158      294       Fernando Mariano Berrio  73.50      30          Panel
    ## 159     1454          Pedro Alvarez Parejo 363.50      90  Camion Grande
    ## 160     1445                  Hector Giron 361.25      30  Camion Grande
    ## 161     1926          Pedro Alvarez Parejo 481.50      30  Camion Grande
    ## 162     1774             Luis Jaime Urbano 443.50      30  Camion Grande
    ## 163     1970              Felipe Villatoro 492.50      90  Camion Grande
    ## 164     1577      Ismael Rodero Monteagudo 394.25      60  Camion Grande
    ## 165      238      Ismael Rodero Monteagudo  59.50      90          Panel
    ## 166      354          Angel Valdez Alegria  88.50      60          Panel
    ## 167     1944       Fernando Mariano Berrio 486.00      60  Camion Grande
    ## 168      970      Ismael Rodero Monteagudo 242.50      90 Camion Pequeño
    ## 169     1993                  Hector Giron 498.25      90  Camion Grande
    ## 170     1777       Fernando Mariano Berrio 444.25      60  Camion Grande
    ## 171     1915             Luis Jaime Urbano 478.75      90  Camion Grande
    ## 172     1267       Fernando Mariano Berrio 316.75      30  Camion Grande
    ## 173      950              Felipe Villatoro 237.50      90 Camion Pequeño
    ## 174     1710        Hector Aragones Frutos 427.50      30  Camion Grande
    ## 175      905              Felipe Villatoro 226.25      90 Camion Pequeño
    ## 176     1866             Luis Jaime Urbano 466.50      60  Camion Grande
    ## 177      210             Luis Jaime Urbano  52.50      60          Panel
    ## 178     1402       Fernando Mariano Berrio 350.50      90  Camion Grande
    ## 179      398             Luis Jaime Urbano  99.50      60          Panel
    ## 180     1172          Pedro Alvarez Parejo 293.00      60  Camion Grande
    ## 181      945          Angel Valdez Alegria 236.25      90 Camion Pequeño
    ## 182      402             Luis Jaime Urbano 100.50      30          Panel
    ## 183      200          Pedro Alvarez Parejo  50.00      90          Panel
    ## 184     1639      Ismael Rodero Monteagudo 409.75      60  Camion Grande
    ## 185      264             Luis Jaime Urbano  66.00      60          Panel
    ## 186      733          Pedro Alvarez Parejo 183.25      60 Camion Pequeño
    ## 187      336              Felipe Villatoro  84.00      90          Panel
    ## 188     1304          Angel Valdez Alegria 326.00      60  Camion Grande
    ## 189      620             Luis Jaime Urbano 155.00      60 Camion Pequeño
    ## 190      693          Angel Valdez Alegria 173.25      30 Camion Pequeño
    ## 191     1480          Angel Valdez Alegria 370.00      30  Camion Grande
    ## 192     1225             Luis Jaime Urbano 306.25      90  Camion Grande
    ## 193      600          Pedro Alvarez Parejo 150.00      60 Camion Pequeño
    ## 194      373       Fernando Mariano Berrio  93.25      60          Panel
    ## 195      442              Felipe Villatoro 110.50      60          Panel
    ## 196     1616       Fernando Mariano Berrio 404.00      30  Camion Grande
    ## 197     1099              Felipe Villatoro 274.75      90  Camion Grande
    ## 198      787              Felipe Villatoro 196.75      30 Camion Pequeño
    ## 199     1314 Juan Francisco Portillo Gomez 328.50      90  Camion Grande
    ## 200      862      Ismael Rodero Monteagudo 215.50      60 Camion Pequeño
    ## 201      445          Pedro Alvarez Parejo 111.25      30          Panel
    ## 202      485      Ismael Rodero Monteagudo 121.25      30          Panel
    ## 203      266        Hector Aragones Frutos  66.50      90          Panel
    ##     mes anio
    ## 1    02 2018
    ## 2    02 2018
    ## 3    02 2018
    ## 4    02 2018
    ## 5    02 2018
    ## 6    02 2018
    ## 7    02 2018
    ## 8    02 2018
    ## 9    02 2018
    ## 10   02 2018
    ## 11   02 2018
    ## 12   02 2018
    ## 13   02 2018
    ## 14   02 2018
    ## 15   02 2018
    ## 16   02 2018
    ## 17   02 2018
    ## 18   02 2018
    ## 19   02 2018
    ## 20   02 2018
    ## 21   02 2018
    ## 22   02 2018
    ## 23   02 2018
    ## 24   02 2018
    ## 25   02 2018
    ## 26   02 2018
    ## 27   02 2018
    ## 28   02 2018
    ## 29   02 2018
    ## 30   02 2018
    ## 31   02 2018
    ## 32   02 2018
    ## 33   02 2018
    ## 34   02 2018
    ## 35   02 2018
    ## 36   02 2018
    ## 37   02 2018
    ## 38   02 2018
    ## 39   02 2018
    ## 40   02 2018
    ## 41   02 2018
    ## 42   02 2018
    ## 43   02 2018
    ## 44   02 2018
    ## 45   02 2018
    ## 46   02 2018
    ## 47   02 2018
    ## 48   02 2018
    ## 49   02 2018
    ## 50   02 2018
    ## 51   02 2018
    ## 52   02 2018
    ## 53   02 2018
    ## 54   02 2018
    ## 55   02 2018
    ## 56   02 2018
    ## 57   02 2018
    ## 58   02 2018
    ## 59   02 2018
    ## 60   02 2018
    ## 61   02 2018
    ## 62   02 2018
    ## 63   02 2018
    ## 64   02 2018
    ## 65   02 2018
    ## 66   02 2018
    ## 67   02 2018
    ## 68   02 2018
    ## 69   02 2018
    ## 70   02 2018
    ## 71   02 2018
    ## 72   02 2018
    ## 73   02 2018
    ## 74   02 2018
    ## 75   02 2018
    ## 76   02 2018
    ## 77   02 2018
    ## 78   02 2018
    ## 79   02 2018
    ## 80   02 2018
    ## 81   02 2018
    ## 82   02 2018
    ## 83   02 2018
    ## 84   02 2018
    ## 85   02 2018
    ## 86   02 2018
    ## 87   02 2018
    ## 88   02 2018
    ## 89   02 2018
    ## 90   02 2018
    ## 91   02 2018
    ## 92   02 2018
    ## 93   02 2018
    ## 94   02 2018
    ## 95   02 2018
    ## 96   02 2018
    ## 97   02 2018
    ## 98   02 2018
    ## 99   02 2018
    ## 100  02 2018
    ## 101  02 2018
    ## 102  02 2018
    ## 103  02 2018
    ## 104  02 2018
    ## 105  02 2018
    ## 106  02 2018
    ## 107  02 2018
    ## 108  02 2018
    ## 109  02 2018
    ## 110  02 2018
    ## 111  02 2018
    ## 112  02 2018
    ## 113  02 2018
    ## 114  02 2018
    ## 115  02 2018
    ## 116  02 2018
    ## 117  02 2018
    ## 118  02 2018
    ## 119  02 2018
    ## 120  02 2018
    ## 121  02 2018
    ## 122  02 2018
    ## 123  02 2018
    ## 124  02 2018
    ## 125  02 2018
    ## 126  02 2018
    ## 127  02 2018
    ## 128  02 2018
    ## 129  02 2018
    ## 130  02 2018
    ## 131  02 2018
    ## 132  02 2018
    ## 133  02 2018
    ## 134  02 2018
    ## 135  02 2018
    ## 136  02 2018
    ## 137  02 2018
    ## 138  02 2018
    ## 139  02 2018
    ## 140  02 2018
    ## 141  02 2018
    ## 142  02 2018
    ## 143  02 2018
    ## 144  02 2018
    ## 145  02 2018
    ## 146  02 2018
    ## 147  02 2018
    ## 148  02 2018
    ## 149  02 2018
    ## 150  02 2018
    ## 151  02 2018
    ## 152  02 2018
    ## 153  02 2018
    ## 154  02 2018
    ## 155  02 2018
    ## 156  02 2018
    ## 157  02 2018
    ## 158  02 2018
    ## 159  02 2018
    ## 160  02 2018
    ## 161  02 2018
    ## 162  02 2018
    ## 163  02 2018
    ## 164  02 2018
    ## 165  02 2018
    ## 166  02 2018
    ## 167  02 2018
    ## 168  02 2018
    ## 169  02 2018
    ## 170  02 2018
    ## 171  02 2018
    ## 172  02 2018
    ## 173  02 2018
    ## 174  02 2018
    ## 175  02 2018
    ## 176  02 2018
    ## 177  02 2018
    ## 178  02 2018
    ## 179  02 2018
    ## 180  02 2018
    ## 181  02 2018
    ## 182  02 2018
    ## 183  02 2018
    ## 184  02 2018
    ## 185  02 2018
    ## 186  02 2018
    ## 187  02 2018
    ## 188  02 2018
    ## 189  02 2018
    ## 190  02 2018
    ## 191  02 2018
    ## 192  02 2018
    ## 193  02 2018
    ## 194  02 2018
    ## 195  02 2018
    ## 196  02 2018
    ## 197  02 2018
    ## 198  02 2018
    ## 199  02 2018
    ## 200  02 2018
    ## 201  02 2018
    ## 202  02 2018
    ## 203  02 2018
    ## 
    ## [[3]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10000396            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 2    10000397           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 3    10000398 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 4    10000399                                     BAR LA OFICINA     76002
    ## 5    10000400                  POLLO PINULITO/Despacho a cliente     76002
    ## 6    10000401        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 7    10000402                                TAQUERIA EL CHINITO     76001
    ## 8    10000403                  POLLO PINULITO/Despacho a cliente     76002
    ## 9    10000404                              HOSPITAL LAS AMERICAS     76002
    ## 10   10000405 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 11   10000406                EL GALLO NEGRO / Despacho a cliente     76002
    ## 12   10000407                     EL PINCHE OBELISCO |||Faltante     76002
    ## 13   10000408 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 14   10000409        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 15   10000410                  POLLO PINULITO/Despacho a cliente     76001
    ## 16   10000411            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 17   10000412        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 18   10000413                            UBIQUO LABS |||FALTANTE     76002
    ## 19   10000414                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 20   10000415                                     BAR LA OFICINA     76002
    ## 21   10000416                                     BAR LA OFICINA     76001
    ## 22   10000417                          POLLO PINULITO|||FALTANTE     76001
    ## 23   10000418            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 24   10000419                              HOSPITAL LAS AMERICAS     76002
    ## 25   10000420                            UBIQUO LABS |||FALTANTE     76001
    ## 26   10000421 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 27   10000422                          POLLO PINULITO|||FALTANTE     76002
    ## 28   10000423                                TAQUERIA EL CHINITO     76001
    ## 29   10000424                                     BAR LA OFICINA     76001
    ## 30   10000425                EL GALLO NEGRO / Despacho a cliente     76002
    ## 31   10000426      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 32   10000427                                        UBIQUO LABS     76001
    ## 33   10000428                          POLLO PINULITO|||FALTANTE     76001
    ## 34   10000429                                     BAR LA OFICINA     76002
    ## 35   10000430 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 36   10000431        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 37   10000432                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 38   10000433      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 39   10000434           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 40   10000435                EL GALLO NEGRO / Despacho a cliente     76002
    ## 41   10000436                                TAQUERIA EL CHINITO     76001
    ## 42   10000437                                     BAR LA OFICINA     76002
    ## 43   10000438        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 44   10000439                  POLLO PINULITO/Despacho a cliente     76002
    ## 45   10000440 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 46   10000441 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 47   10000442                EL GALLO NEGRO / Despacho a cliente     76001
    ## 48   10000443      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 49   10000444 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 50   10000445                                     BAR LA OFICINA     76001
    ## 51   10000446                                TAQUERIA EL CHINITO     76002
    ## 52   10000447                                TAQUERIA EL CHINITO     76002
    ## 53   10000448        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 54   10000449                                     BAR LA OFICINA     76001
    ## 55   10000450           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 56   10000451            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 57   10000452                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 58   10000453                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 59   10000454      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 60   10000455            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 61   10000456                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 62   10000457           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 63   10000458      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 64   10000459                     EL PINCHE OBELISCO |||Faltante     76001
    ## 65   10000460                     EL PINCHE OBELISCO |||Faltante     76002
    ## 66   10000461 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 67   10000462                     EL PINCHE OBELISCO |||Faltante     76001
    ## 68   10000463                          POLLO PINULITO|||FALTANTE     76001
    ## 69   10000464                                        UBIQUO LABS     76002
    ## 70   10000465                          POLLO PINULITO|||FALTANTE     76002
    ## 71   10000466                                TAQUERIA EL CHINITO     76001
    ## 72   10000467                                        UBIQUO LABS     76001
    ## 73   10000468                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 74   10000469           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 75   10000470                                        UBIQUO LABS     76001
    ## 76   10000471                              HOSPITAL LAS AMERICAS     76001
    ## 77   10000472                                        UBIQUO LABS     76002
    ## 78   10000473        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 79   10000474            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 80   10000475                                        UBIQUO LABS     76002
    ## 81   10000476                EL GALLO NEGRO / Despacho a cliente     76001
    ## 82   10000477                EL GALLO NEGRO / Despacho a cliente     76001
    ## 83   10000478           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 84   10000479            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 85   10000480                EL GALLO NEGRO / Despacho a cliente     76001
    ## 86   10000481                     EL PINCHE OBELISCO |||Faltante     76002
    ## 87   10000482            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 88   10000483      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 89   10000484            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 90   10000485                  POLLO PINULITO/Despacho a cliente     76001
    ## 91   10000486            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 92   10000487            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 93   10000488                            UBIQUO LABS |||FALTANTE     76001
    ## 94   10000489                EL GALLO NEGRO / Despacho a cliente     76002
    ## 95   10000490                  POLLO PINULITO/Despacho a cliente     76001
    ## 96   10000491            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 97   10000492                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 98   10000493           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 99   10000494           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 100  10000495                EL GALLO NEGRO / Despacho a cliente     76002
    ## 101  10000496                                     BAR LA OFICINA     76002
    ## 102  10000497                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 103  10000498                                        UBIQUO LABS     76002
    ## 104  10000499            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 105  10000500                          POLLO PINULITO|||FALTANTE     76002
    ## 106  10000501                     EL PINCHE OBELISCO |||Faltante     76002
    ## 107  10000502           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 108  10000503        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 109  10000504                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 110  10000505                            UBIQUO LABS |||FALTANTE     76002
    ## 111  10000506                                     BAR LA OFICINA     76002
    ## 112  10000507           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 113  10000508                EL GALLO NEGRO / Despacho a cliente     76002
    ## 114  10000509                     EL PINCHE OBELISCO |||Faltante     76002
    ## 115  10000510                EL GALLO NEGRO / Despacho a cliente     76002
    ## 116  10000511                            UBIQUO LABS |||FALTANTE     76001
    ## 117  10000512                                TAQUERIA EL CHINITO     76001
    ## 118  10000513           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 119  10000514                            UBIQUO LABS |||FALTANTE     76002
    ## 120  10000515            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 121  10000516            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 122  10000517                              HOSPITAL LAS AMERICAS     76002
    ## 123  10000518           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 124  10000519                            UBIQUO LABS |||FALTANTE     76001
    ## 125  10000520            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 126  10000521                                     BAR LA OFICINA     76001
    ## 127  10000522                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 128  10000523            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 129  10000524                                     BAR LA OFICINA     76001
    ## 130  10000525            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 131  10000526            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 132  10000527            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 133  10000528                          POLLO PINULITO|||FALTANTE     76002
    ## 134  10000529                                        UBIQUO LABS     76001
    ## 135  10000530      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 136  10000531                            UBIQUO LABS |||FALTANTE     76002
    ## 137  10000532                            UBIQUO LABS |||FALTANTE     76002
    ## 138  10000533                              HOSPITAL LAS AMERICAS     76001
    ## 139  10000534                     EL PINCHE OBELISCO |||Faltante     76001
    ## 140  10000535                            UBIQUO LABS |||FALTANTE     76001
    ## 141  10000536                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 142  10000537                          POLLO PINULITO|||FALTANTE     76001
    ## 143  10000538           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 144  10000539 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 145  10000540 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 146  10000541                                     BAR LA OFICINA     76001
    ## 147  10000542                  POLLO PINULITO/Despacho a cliente     76001
    ## 148  10000543                EL GALLO NEGRO / Despacho a cliente     76002
    ## 149  10000544      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 150  10000545                          POLLO PINULITO|||FALTANTE     76002
    ## 151  10000546                                        UBIQUO LABS     76002
    ## 152  10000547                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 153  10000548                                     BAR LA OFICINA     76002
    ## 154  10000549           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 155  10000550                                     BAR LA OFICINA     76002
    ## 156  10000551                     EL PINCHE OBELISCO |||Faltante     76001
    ## 157  10000552                     EL PINCHE OBELISCO |||Faltante     76002
    ## 158  10000553                              HOSPITAL LAS AMERICAS     76002
    ## 159  10000554                EL GALLO NEGRO / Despacho a cliente     76001
    ## 160  10000555                                TAQUERIA EL CHINITO     76002
    ## 161  10000556 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 162  10000557                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 163  10000558            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 164  10000559           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 165  10000560                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 166  10000561        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 167  10000562        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 168  10000563           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 169  10000564                          POLLO PINULITO|||FALTANTE     76001
    ## 170  10000565                EL GALLO NEGRO / Despacho a cliente     76001
    ## 171  10000566                EL GALLO NEGRO / Despacho a cliente     76002
    ## 172  10000567                                TAQUERIA EL CHINITO     76001
    ## 173  10000568                  POLLO PINULITO/Despacho a cliente     76002
    ## 174  10000569                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 175  10000570 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 176  10000571                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 177  10000572                                TAQUERIA EL CHINITO     76001
    ## 178  10000573                EL GALLO NEGRO / Despacho a cliente     76001
    ## 179  10000574        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 180  10000575                                        UBIQUO LABS     76001
    ## 181  10000576                                        UBIQUO LABS     76001
    ## 182  10000577                                TAQUERIA EL CHINITO     76002
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1979      Ismael Rodero Monteagudo 494.75      30  Camion Grande
    ## 2       1116              Felipe Villatoro 279.00      30  Camion Grande
    ## 3        384          Angel Valdez Alegria  96.00      90          Panel
    ## 4        599 Juan Francisco Portillo Gomez 149.75      30 Camion Pequeño
    ## 5        388                  Hector Giron  97.00      90          Panel
    ## 6       1164        Hector Aragones Frutos 291.00      30  Camion Grande
    ## 7       1945       Fernando Mariano Berrio 486.25      90  Camion Grande
    ## 8        724 Juan Francisco Portillo Gomez 181.00      60 Camion Pequeño
    ## 9        412          Angel Valdez Alegria 103.00      60          Panel
    ## 10       807 Juan Francisco Portillo Gomez 201.75      60 Camion Pequeño
    ## 11      1950       Fernando Mariano Berrio 487.50      90  Camion Grande
    ## 12      1957      Ismael Rodero Monteagudo 489.25      30  Camion Grande
    ## 13      1664      Ismael Rodero Monteagudo 416.00      30  Camion Grande
    ## 14      1126             Luis Jaime Urbano 281.50      30  Camion Grande
    ## 15      1328              Felipe Villatoro 332.00      90  Camion Grande
    ## 16       336      Ismael Rodero Monteagudo  84.00      30          Panel
    ## 17      1893          Pedro Alvarez Parejo 473.25      60  Camion Grande
    ## 18       680       Fernando Mariano Berrio 170.00      90 Camion Pequeño
    ## 19      1092        Hector Aragones Frutos 273.00      90  Camion Grande
    ## 20      1174              Felipe Villatoro 293.50      90  Camion Grande
    ## 21       737 Juan Francisco Portillo Gomez 184.25      30 Camion Pequeño
    ## 22       484       Fernando Mariano Berrio 121.00      60          Panel
    ## 23       948       Fernando Mariano Berrio 237.00      60 Camion Pequeño
    ## 24      1312             Luis Jaime Urbano 328.00      90  Camion Grande
    ## 25      1030              Felipe Villatoro 257.50      90  Camion Grande
    ## 26      1903          Pedro Alvarez Parejo 475.75      30  Camion Grande
    ## 27       492 Juan Francisco Portillo Gomez 123.00      30          Panel
    ## 28      1285       Fernando Mariano Berrio 321.25      60  Camion Grande
    ## 29       462              Felipe Villatoro 115.50      90          Panel
    ## 30       294 Juan Francisco Portillo Gomez  73.50      30          Panel
    ## 31      1722                  Hector Giron 430.50      60  Camion Grande
    ## 32       436              Felipe Villatoro 109.00      60          Panel
    ## 33       271       Fernando Mariano Berrio  67.75      60          Panel
    ## 34      1905        Hector Aragones Frutos 476.25      90  Camion Grande
    ## 35       833      Ismael Rodero Monteagudo 208.25      30 Camion Pequeño
    ## 36       224             Luis Jaime Urbano  56.00      60          Panel
    ## 37       703      Ismael Rodero Monteagudo 175.75      60 Camion Pequeño
    ## 38       464      Ismael Rodero Monteagudo 116.00      60          Panel
    ## 39      1238      Ismael Rodero Monteagudo 309.50      60  Camion Grande
    ## 40       462              Felipe Villatoro 115.50      60          Panel
    ## 41      1917             Luis Jaime Urbano 479.25      30  Camion Grande
    ## 42       248      Ismael Rodero Monteagudo  62.00      90          Panel
    ## 43      1270             Luis Jaime Urbano 317.50      90  Camion Grande
    ## 44      1973          Angel Valdez Alegria 493.25      60  Camion Grande
    ## 45       864        Hector Aragones Frutos 216.00      90 Camion Pequeño
    ## 46       424       Fernando Mariano Berrio 106.00      60          Panel
    ## 47       312        Hector Aragones Frutos  78.00      60          Panel
    ## 48      1788      Ismael Rodero Monteagudo 447.00      60  Camion Grande
    ## 49      1186        Hector Aragones Frutos 296.50      90  Camion Grande
    ## 50       414          Pedro Alvarez Parejo 103.50      30          Panel
    ## 51       519                  Hector Giron 129.75      30 Camion Pequeño
    ## 52      1495       Fernando Mariano Berrio 373.75      30  Camion Grande
    ## 53       769                  Hector Giron 192.25      90 Camion Pequeño
    ## 54      1381          Angel Valdez Alegria 345.25      30  Camion Grande
    ## 55       690          Pedro Alvarez Parejo 172.50      30 Camion Pequeño
    ## 56      1593      Ismael Rodero Monteagudo 398.25      30  Camion Grande
    ## 57      1433             Luis Jaime Urbano 358.25      90  Camion Grande
    ## 58       713        Hector Aragones Frutos 178.25      60 Camion Pequeño
    ## 59       636                  Hector Giron 159.00      60 Camion Pequeño
    ## 60       638        Hector Aragones Frutos 159.50      60 Camion Pequeño
    ## 61      1708                  Hector Giron 427.00      30  Camion Grande
    ## 62      1202             Luis Jaime Urbano 300.50      30  Camion Grande
    ## 63       602          Angel Valdez Alegria 150.50      60 Camion Pequeño
    ## 64       323        Hector Aragones Frutos  80.75      60          Panel
    ## 65       320      Ismael Rodero Monteagudo  80.00      60          Panel
    ## 66       381              Felipe Villatoro  95.25      60          Panel
    ## 67       535          Angel Valdez Alegria 133.75      60 Camion Pequeño
    ## 68       562             Luis Jaime Urbano 140.50      30 Camion Pequeño
    ## 69       950       Fernando Mariano Berrio 237.50      30 Camion Pequeño
    ## 70      1883      Ismael Rodero Monteagudo 470.75      60  Camion Grande
    ## 71      1690       Fernando Mariano Berrio 422.50      30  Camion Grande
    ## 72      1327              Felipe Villatoro 331.75      90  Camion Grande
    ## 73      1458             Luis Jaime Urbano 364.50      30  Camion Grande
    ## 74      1059          Angel Valdez Alegria 264.75      30  Camion Grande
    ## 75      1002             Luis Jaime Urbano 250.50      30  Camion Grande
    ## 76      1302          Angel Valdez Alegria 325.50      30  Camion Grande
    ## 77      1639      Ismael Rodero Monteagudo 409.75      60  Camion Grande
    ## 78       840        Hector Aragones Frutos 210.00      60 Camion Pequeño
    ## 79      1849             Luis Jaime Urbano 462.25      30  Camion Grande
    ## 80      1065             Luis Jaime Urbano 266.25      60  Camion Grande
    ## 81      1529      Ismael Rodero Monteagudo 382.25      60  Camion Grande
    ## 82       337      Ismael Rodero Monteagudo  84.25      90          Panel
    ## 83       719        Hector Aragones Frutos 179.75      30 Camion Pequeño
    ## 84      1913                  Hector Giron 478.25      90  Camion Grande
    ## 85      1180          Pedro Alvarez Parejo 295.00      30  Camion Grande
    ## 86      1052          Pedro Alvarez Parejo 263.00      30  Camion Grande
    ## 87      1037          Pedro Alvarez Parejo 259.25      90  Camion Grande
    ## 88      1953      Ismael Rodero Monteagudo 488.25      30  Camion Grande
    ## 89      1083       Fernando Mariano Berrio 270.75      90  Camion Grande
    ## 90      1482              Felipe Villatoro 370.50      30  Camion Grande
    ## 91      1681          Angel Valdez Alegria 420.25      30  Camion Grande
    ## 92      1418      Ismael Rodero Monteagudo 354.50      30  Camion Grande
    ## 93      1285          Angel Valdez Alegria 321.25      60  Camion Grande
    ## 94       878      Ismael Rodero Monteagudo 219.50      90 Camion Pequeño
    ## 95       332          Angel Valdez Alegria  83.00      30          Panel
    ## 96       256             Luis Jaime Urbano  64.00      30          Panel
    ## 97      1724              Felipe Villatoro 431.00      60  Camion Grande
    ## 98      1996          Angel Valdez Alegria 499.00      90  Camion Grande
    ## 99      1097                  Hector Giron 274.25      60  Camion Grande
    ## 100     1009              Felipe Villatoro 252.25      90  Camion Grande
    ## 101     1730       Fernando Mariano Berrio 432.50      60  Camion Grande
    ## 102     1718 Juan Francisco Portillo Gomez 429.50      30  Camion Grande
    ## 103     1720        Hector Aragones Frutos 430.00      60  Camion Grande
    ## 104     1737             Luis Jaime Urbano 434.25      90  Camion Grande
    ## 105      590          Angel Valdez Alegria 147.50      60 Camion Pequeño
    ## 106     1040             Luis Jaime Urbano 260.00      60  Camion Grande
    ## 107      443             Luis Jaime Urbano 110.75      90          Panel
    ## 108     1020      Ismael Rodero Monteagudo 255.00      60  Camion Grande
    ## 109     1309          Pedro Alvarez Parejo 327.25      30  Camion Grande
    ## 110      611      Ismael Rodero Monteagudo 152.75      60 Camion Pequeño
    ## 111     1941          Pedro Alvarez Parejo 485.25      60  Camion Grande
    ## 112      790                  Hector Giron 197.50      30 Camion Pequeño
    ## 113      372              Felipe Villatoro  93.00      30          Panel
    ## 114     1808 Juan Francisco Portillo Gomez 452.00      30  Camion Grande
    ## 115      996       Fernando Mariano Berrio 249.00      60 Camion Pequeño
    ## 116     1580      Ismael Rodero Monteagudo 395.00      90  Camion Grande
    ## 117     1580             Luis Jaime Urbano 395.00      60  Camion Grande
    ## 118     1276              Felipe Villatoro 319.00      90  Camion Grande
    ## 119     1683       Fernando Mariano Berrio 420.75      60  Camion Grande
    ## 120     1055      Ismael Rodero Monteagudo 263.75      30  Camion Grande
    ## 121      814              Felipe Villatoro 203.50      30 Camion Pequeño
    ## 122      397        Hector Aragones Frutos  99.25      30          Panel
    ## 123     1386        Hector Aragones Frutos 346.50      60  Camion Grande
    ## 124     1960          Angel Valdez Alegria 490.00      90  Camion Grande
    ## 125      229       Fernando Mariano Berrio  57.25      90          Panel
    ## 126      831 Juan Francisco Portillo Gomez 207.75      60 Camion Pequeño
    ## 127     1720        Hector Aragones Frutos 430.00      30  Camion Grande
    ## 128     1811       Fernando Mariano Berrio 452.75      30  Camion Grande
    ## 129      319              Felipe Villatoro  79.75      30          Panel
    ## 130     1414             Luis Jaime Urbano 353.50      60  Camion Grande
    ## 131     1097        Hector Aragones Frutos 274.25      90  Camion Grande
    ## 132     1859      Ismael Rodero Monteagudo 464.75      90  Camion Grande
    ## 133      440      Ismael Rodero Monteagudo 110.00      90          Panel
    ## 134      499        Hector Aragones Frutos 124.75      60          Panel
    ## 135     1396 Juan Francisco Portillo Gomez 349.00      90  Camion Grande
    ## 136      403                  Hector Giron 100.75      60          Panel
    ## 137     1445                  Hector Giron 361.25      30  Camion Grande
    ## 138      378              Felipe Villatoro  94.50      30          Panel
    ## 139      924       Fernando Mariano Berrio 231.00      60 Camion Pequeño
    ## 140     1444              Felipe Villatoro 361.00      90  Camion Grande
    ## 141      253          Angel Valdez Alegria  63.25      60          Panel
    ## 142     1947       Fernando Mariano Berrio 486.75      30  Camion Grande
    ## 143     1563              Felipe Villatoro 390.75      30  Camion Grande
    ## 144      742        Hector Aragones Frutos 185.50      30 Camion Pequeño
    ## 145      243              Felipe Villatoro  60.75      90          Panel
    ## 146     1506 Juan Francisco Portillo Gomez 376.50      30  Camion Grande
    ## 147     1889       Fernando Mariano Berrio 472.25      60  Camion Grande
    ## 148      531          Pedro Alvarez Parejo 132.75      90 Camion Pequeño
    ## 149     1037          Angel Valdez Alegria 259.25      90  Camion Grande
    ## 150     1692        Hector Aragones Frutos 423.00      30  Camion Grande
    ## 151      894              Felipe Villatoro 223.50      60 Camion Pequeño
    ## 152      504       Fernando Mariano Berrio 126.00      60 Camion Pequeño
    ## 153      665        Hector Aragones Frutos 166.25      30 Camion Pequeño
    ## 154      964          Angel Valdez Alegria 241.00      90 Camion Pequeño
    ## 155      743          Pedro Alvarez Parejo 185.75      30 Camion Pequeño
    ## 156     1193      Ismael Rodero Monteagudo 298.25      30  Camion Grande
    ## 157     1865       Fernando Mariano Berrio 466.25      60  Camion Grande
    ## 158     1456      Ismael Rodero Monteagudo 364.00      60  Camion Grande
    ## 159      772             Luis Jaime Urbano 193.00      30 Camion Pequeño
    ## 160      385 Juan Francisco Portillo Gomez  96.25      90          Panel
    ## 161      591       Fernando Mariano Berrio 147.75      30 Camion Pequeño
    ## 162     1241             Luis Jaime Urbano 310.25      90  Camion Grande
    ## 163      794          Angel Valdez Alegria 198.50      90 Camion Pequeño
    ## 164     1944      Ismael Rodero Monteagudo 486.00      60  Camion Grande
    ## 165     1355              Felipe Villatoro 338.75      60  Camion Grande
    ## 166      474          Angel Valdez Alegria 118.50      90          Panel
    ## 167     1014          Pedro Alvarez Parejo 253.50      60  Camion Grande
    ## 168      906              Felipe Villatoro 226.50      90 Camion Pequeño
    ## 169      408       Fernando Mariano Berrio 102.00      30          Panel
    ## 170      873                  Hector Giron 218.25      90 Camion Pequeño
    ## 171      905             Luis Jaime Urbano 226.25      90 Camion Pequeño
    ## 172     1249             Luis Jaime Urbano 312.25      30  Camion Grande
    ## 173     1040        Hector Aragones Frutos 260.00      90  Camion Grande
    ## 174      467        Hector Aragones Frutos 116.75      30          Panel
    ## 175     1294      Ismael Rodero Monteagudo 323.50      30  Camion Grande
    ## 176     1497             Luis Jaime Urbano 374.25      30  Camion Grande
    ## 177     1481                  Hector Giron 370.25      90  Camion Grande
    ## 178     1378          Angel Valdez Alegria 344.50      90  Camion Grande
    ## 179      809          Pedro Alvarez Parejo 202.25      90 Camion Pequeño
    ## 180      856      Ismael Rodero Monteagudo 214.00      90 Camion Pequeño
    ## 181      558        Hector Aragones Frutos 139.50      30 Camion Pequeño
    ## 182      280                  Hector Giron  70.00      90          Panel
    ##     mes anio
    ## 1    03 2018
    ## 2    03 2018
    ## 3    03 2018
    ## 4    03 2018
    ## 5    03 2018
    ## 6    03 2018
    ## 7    03 2018
    ## 8    03 2018
    ## 9    03 2018
    ## 10   03 2018
    ## 11   03 2018
    ## 12   03 2018
    ## 13   03 2018
    ## 14   03 2018
    ## 15   03 2018
    ## 16   03 2018
    ## 17   03 2018
    ## 18   03 2018
    ## 19   03 2018
    ## 20   03 2018
    ## 21   03 2018
    ## 22   03 2018
    ## 23   03 2018
    ## 24   03 2018
    ## 25   03 2018
    ## 26   03 2018
    ## 27   03 2018
    ## 28   03 2018
    ## 29   03 2018
    ## 30   03 2018
    ## 31   03 2018
    ## 32   03 2018
    ## 33   03 2018
    ## 34   03 2018
    ## 35   03 2018
    ## 36   03 2018
    ## 37   03 2018
    ## 38   03 2018
    ## 39   03 2018
    ## 40   03 2018
    ## 41   03 2018
    ## 42   03 2018
    ## 43   03 2018
    ## 44   03 2018
    ## 45   03 2018
    ## 46   03 2018
    ## 47   03 2018
    ## 48   03 2018
    ## 49   03 2018
    ## 50   03 2018
    ## 51   03 2018
    ## 52   03 2018
    ## 53   03 2018
    ## 54   03 2018
    ## 55   03 2018
    ## 56   03 2018
    ## 57   03 2018
    ## 58   03 2018
    ## 59   03 2018
    ## 60   03 2018
    ## 61   03 2018
    ## 62   03 2018
    ## 63   03 2018
    ## 64   03 2018
    ## 65   03 2018
    ## 66   03 2018
    ## 67   03 2018
    ## 68   03 2018
    ## 69   03 2018
    ## 70   03 2018
    ## 71   03 2018
    ## 72   03 2018
    ## 73   03 2018
    ## 74   03 2018
    ## 75   03 2018
    ## 76   03 2018
    ## 77   03 2018
    ## 78   03 2018
    ## 79   03 2018
    ## 80   03 2018
    ## 81   03 2018
    ## 82   03 2018
    ## 83   03 2018
    ## 84   03 2018
    ## 85   03 2018
    ## 86   03 2018
    ## 87   03 2018
    ## 88   03 2018
    ## 89   03 2018
    ## 90   03 2018
    ## 91   03 2018
    ## 92   03 2018
    ## 93   03 2018
    ## 94   03 2018
    ## 95   03 2018
    ## 96   03 2018
    ## 97   03 2018
    ## 98   03 2018
    ## 99   03 2018
    ## 100  03 2018
    ## 101  03 2018
    ## 102  03 2018
    ## 103  03 2018
    ## 104  03 2018
    ## 105  03 2018
    ## 106  03 2018
    ## 107  03 2018
    ## 108  03 2018
    ## 109  03 2018
    ## 110  03 2018
    ## 111  03 2018
    ## 112  03 2018
    ## 113  03 2018
    ## 114  03 2018
    ## 115  03 2018
    ## 116  03 2018
    ## 117  03 2018
    ## 118  03 2018
    ## 119  03 2018
    ## 120  03 2018
    ## 121  03 2018
    ## 122  03 2018
    ## 123  03 2018
    ## 124  03 2018
    ## 125  03 2018
    ## 126  03 2018
    ## 127  03 2018
    ## 128  03 2018
    ## 129  03 2018
    ## 130  03 2018
    ## 131  03 2018
    ## 132  03 2018
    ## 133  03 2018
    ## 134  03 2018
    ## 135  03 2018
    ## 136  03 2018
    ## 137  03 2018
    ## 138  03 2018
    ## 139  03 2018
    ## 140  03 2018
    ## 141  03 2018
    ## 142  03 2018
    ## 143  03 2018
    ## 144  03 2018
    ## 145  03 2018
    ## 146  03 2018
    ## 147  03 2018
    ## 148  03 2018
    ## 149  03 2018
    ## 150  03 2018
    ## 151  03 2018
    ## 152  03 2018
    ## 153  03 2018
    ## 154  03 2018
    ## 155  03 2018
    ## 156  03 2018
    ## 157  03 2018
    ## 158  03 2018
    ## 159  03 2018
    ## 160  03 2018
    ## 161  03 2018
    ## 162  03 2018
    ## 163  03 2018
    ## 164  03 2018
    ## 165  03 2018
    ## 166  03 2018
    ## 167  03 2018
    ## 168  03 2018
    ## 169  03 2018
    ## 170  03 2018
    ## 171  03 2018
    ## 172  03 2018
    ## 173  03 2018
    ## 174  03 2018
    ## 175  03 2018
    ## 176  03 2018
    ## 177  03 2018
    ## 178  03 2018
    ## 179  03 2018
    ## 180  03 2018
    ## 181  03 2018
    ## 182  03 2018
    ## 
    ## [[4]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10000578 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 2    10000579                          POLLO PINULITO|||FALTANTE     76001
    ## 3    10000580                            UBIQUO LABS |||FALTANTE     76002
    ## 4    10000581      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 5    10000582      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 6    10000583                              HOSPITAL LAS AMERICAS     76002
    ## 7    10000584                            UBIQUO LABS |||FALTANTE     76002
    ## 8    10000585 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 9    10000586            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 10   10000587                     EL PINCHE OBELISCO |||Faltante     76002
    ## 11   10000588                                     BAR LA OFICINA     76001
    ## 12   10000589            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 13   10000590           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 14   10000591            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 15   10000592                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 16   10000593                            UBIQUO LABS |||FALTANTE     76001
    ## 17   10000594                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 18   10000595                                TAQUERIA EL CHINITO     76002
    ## 19   10000596                                        UBIQUO LABS     76001
    ## 20   10000597                  POLLO PINULITO/Despacho a cliente     76002
    ## 21   10000598                     EL PINCHE OBELISCO |||Faltante     76002
    ## 22   10000599                              HOSPITAL LAS AMERICAS     76002
    ## 23   10000600                  POLLO PINULITO/Despacho a cliente     76002
    ## 24   10000601                     EL PINCHE OBELISCO |||Faltante     76001
    ## 25   10000602      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 26   10000603                     EL PINCHE OBELISCO |||Faltante     76001
    ## 27   10000604                                        UBIQUO LABS     76001
    ## 28   10000605                            UBIQUO LABS |||FALTANTE     76001
    ## 29   10000606 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 30   10000607                                     BAR LA OFICINA     76001
    ## 31   10000608                              HOSPITAL LAS AMERICAS     76002
    ## 32   10000609                              HOSPITAL LAS AMERICAS     76001
    ## 33   10000610                                TAQUERIA EL CHINITO     76001
    ## 34   10000611            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 35   10000612        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 36   10000613                  POLLO PINULITO/Despacho a cliente     76001
    ## 37   10000614            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 38   10000615        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 39   10000616                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 40   10000617                            UBIQUO LABS |||FALTANTE     76002
    ## 41   10000618                                        UBIQUO LABS     76001
    ## 42   10000619                                     BAR LA OFICINA     76001
    ## 43   10000620                                     BAR LA OFICINA     76002
    ## 44   10000621                          POLLO PINULITO|||FALTANTE     76002
    ## 45   10000622                  POLLO PINULITO/Despacho a cliente     76002
    ## 46   10000623           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 47   10000624                                TAQUERIA EL CHINITO     76002
    ## 48   10000625                  POLLO PINULITO/Despacho a cliente     76002
    ## 49   10000626                            UBIQUO LABS |||FALTANTE     76001
    ## 50   10000627                                        UBIQUO LABS     76001
    ## 51   10000628      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 52   10000629           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 53   10000630 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 54   10000631        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 55   10000632 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 56   10000633                          POLLO PINULITO|||FALTANTE     76001
    ## 57   10000634                  POLLO PINULITO/Despacho a cliente     76002
    ## 58   10000635 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 59   10000636            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 60   10000637                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 61   10000638                  POLLO PINULITO/Despacho a cliente     76001
    ## 62   10000639 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 63   10000640            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 64   10000641                                     BAR LA OFICINA     76002
    ## 65   10000642                EL GALLO NEGRO / Despacho a cliente     76001
    ## 66   10000643                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 67   10000644                                TAQUERIA EL CHINITO     76001
    ## 68   10000645      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 69   10000646                                        UBIQUO LABS     76002
    ## 70   10000647                                     BAR LA OFICINA     76002
    ## 71   10000648                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 72   10000649           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 73   10000650                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 74   10000651                                        UBIQUO LABS     76002
    ## 75   10000652                            UBIQUO LABS |||FALTANTE     76001
    ## 76   10000653                                        UBIQUO LABS     76002
    ## 77   10000654            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 78   10000655            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 79   10000656                  POLLO PINULITO/Despacho a cliente     76002
    ## 80   10000657           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 81   10000658                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 82   10000659            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 83   10000660           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 84   10000661        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 85   10000662           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 86   10000663                EL GALLO NEGRO / Despacho a cliente     76002
    ## 87   10000664                                TAQUERIA EL CHINITO     76002
    ## 88   10000665                                        UBIQUO LABS     76002
    ## 89   10000666        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 90   10000667                EL GALLO NEGRO / Despacho a cliente     76001
    ## 91   10000668                                        UBIQUO LABS     76002
    ## 92   10000669 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 93   10000670                     EL PINCHE OBELISCO |||Faltante     76002
    ## 94   10000671                     EL PINCHE OBELISCO |||Faltante     76002
    ## 95   10000672                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 96   10000673                                TAQUERIA EL CHINITO     76002
    ## 97   10000674 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 98   10000675                     EL PINCHE OBELISCO |||Faltante     76002
    ## 99   10000676        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 100  10000677                              HOSPITAL LAS AMERICAS     76002
    ## 101  10000678                EL GALLO NEGRO / Despacho a cliente     76002
    ## 102  10000679 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 103  10000680            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 104  10000681                                        UBIQUO LABS     76001
    ## 105  10000682                                        UBIQUO LABS     76002
    ## 106  10000683      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 107  10000684            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 108  10000685                     EL PINCHE OBELISCO |||Faltante     76001
    ## 109  10000686                  POLLO PINULITO/Despacho a cliente     76001
    ## 110  10000687                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 111  10000688            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 112  10000689        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 113  10000690                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 114  10000691                EL GALLO NEGRO / Despacho a cliente     76002
    ## 115  10000692                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 116  10000693                                        UBIQUO LABS     76002
    ## 117  10000694                EL GALLO NEGRO / Despacho a cliente     76002
    ## 118  10000695           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 119  10000696                     EL PINCHE OBELISCO |||Faltante     76001
    ## 120  10000697            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 121  10000698            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 122  10000699            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 123  10000700            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 124  10000701           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 125  10000702                  POLLO PINULITO/Despacho a cliente     76002
    ## 126  10000703                  POLLO PINULITO/Despacho a cliente     76002
    ## 127  10000704 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 128  10000705                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 129  10000706                                     BAR LA OFICINA     76002
    ## 130  10000707                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 131  10000708                EL GALLO NEGRO / Despacho a cliente     76002
    ## 132  10000709                  POLLO PINULITO/Despacho a cliente     76001
    ## 133  10000710                                     BAR LA OFICINA     76001
    ## 134  10000711                                        UBIQUO LABS     76001
    ## 135  10000712            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 136  10000713                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 137  10000714                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 138  10000715      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 139  10000716      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 140  10000717                                     BAR LA OFICINA     76002
    ## 141  10000718        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 142  10000719           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 143  10000720                                     BAR LA OFICINA     76002
    ## 144  10000721      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 145  10000722        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 146  10000723           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 147  10000724 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 148  10000725                          POLLO PINULITO|||FALTANTE     76002
    ## 149  10000726                                TAQUERIA EL CHINITO     76001
    ## 150  10000727        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 151  10000728                                        UBIQUO LABS     76002
    ## 152  10000729      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 153  10000730                                        UBIQUO LABS     76001
    ## 154  10000731                     EL PINCHE OBELISCO |||Faltante     76001
    ## 155  10000732                                        UBIQUO LABS     76001
    ## 156  10000733                EL GALLO NEGRO / Despacho a cliente     76001
    ## 157  10000734                                        UBIQUO LABS     76001
    ## 158  10000735                  POLLO PINULITO/Despacho a cliente     76002
    ## 159  10000736                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 160  10000737        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 161  10000738                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 162  10000739           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 163  10000740           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 164  10000741      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 165  10000742 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 166  10000743                          POLLO PINULITO|||FALTANTE     76001
    ## 167  10000744                            UBIQUO LABS |||FALTANTE     76001
    ## 168  10000745            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 169  10000746                                     BAR LA OFICINA     76002
    ## 170  10000747            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 171  10000748 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 172  10000749                              HOSPITAL LAS AMERICAS     76002
    ## 173  10000750                            UBIQUO LABS |||FALTANTE     76001
    ## 174  10000751                  POLLO PINULITO/Despacho a cliente     76001
    ## 175  10000752      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 176  10000753 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 177  10000754                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 178  10000755                                TAQUERIA EL CHINITO     76002
    ## 179  10000756                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 180  10000757                                     BAR LA OFICINA     76002
    ## 181  10000758            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 182  10000759                            UBIQUO LABS |||FALTANTE     76002
    ## 183  10000760                EL GALLO NEGRO / Despacho a cliente     76002
    ## 184  10000761                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 185  10000762           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 186  10000763                                     BAR LA OFICINA     76002
    ## 187  10000764                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 188  10000765 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 189  10000766                EL GALLO NEGRO / Despacho a cliente     76002
    ## 190  10000767                     EL PINCHE OBELISCO |||Faltante     76001
    ## 191  10000768 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 192  10000769                     EL PINCHE OBELISCO |||Faltante     76002
    ## 193  10000770            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 194  10000771                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 195  10000772        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 196  10000773                                     BAR LA OFICINA     76002
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1049          Angel Valdez Alegria 262.25      60  Camion Grande
    ## 2        533              Felipe Villatoro 133.25      90 Camion Pequeño
    ## 3       1788                  Hector Giron 447.00      90  Camion Grande
    ## 4       1987             Luis Jaime Urbano 496.75      60  Camion Grande
    ## 5        649              Felipe Villatoro 162.25      30 Camion Pequeño
    ## 6        924        Hector Aragones Frutos 231.00      30 Camion Pequeño
    ## 7       1086      Ismael Rodero Monteagudo 271.50      90  Camion Grande
    ## 8       1505          Angel Valdez Alegria 376.25      30  Camion Grande
    ## 9       1532             Luis Jaime Urbano 383.00      90  Camion Grande
    ## 10       502          Pedro Alvarez Parejo 125.50      90 Camion Pequeño
    ## 11      1108                  Hector Giron 277.00      90  Camion Grande
    ## 12      1197             Luis Jaime Urbano 299.25      90  Camion Grande
    ## 13       761       Fernando Mariano Berrio 190.25      30 Camion Pequeño
    ## 14      1274                  Hector Giron 318.50      30  Camion Grande
    ## 15       826          Pedro Alvarez Parejo 206.50      30 Camion Pequeño
    ## 16       485        Hector Aragones Frutos 121.25      60          Panel
    ## 17       311          Pedro Alvarez Parejo  77.75      90          Panel
    ## 18      1457          Pedro Alvarez Parejo 364.25      60  Camion Grande
    ## 19       410             Luis Jaime Urbano 102.50      30          Panel
    ## 20      1679       Fernando Mariano Berrio 419.75      90  Camion Grande
    ## 21       700          Pedro Alvarez Parejo 175.00      60 Camion Pequeño
    ## 22       809          Pedro Alvarez Parejo 202.25      60 Camion Pequeño
    ## 23       529          Pedro Alvarez Parejo 132.25      90 Camion Pequeño
    ## 24      1078        Hector Aragones Frutos 269.50      90  Camion Grande
    ## 25      1086          Angel Valdez Alegria 271.50      60  Camion Grande
    ## 26       465              Felipe Villatoro 116.25      90          Panel
    ## 27       291        Hector Aragones Frutos  72.75      30          Panel
    ## 28      1684                  Hector Giron 421.00      60  Camion Grande
    ## 29       455      Ismael Rodero Monteagudo 113.75      60          Panel
    ## 30      1131          Pedro Alvarez Parejo 282.75      60  Camion Grande
    ## 31      1104              Felipe Villatoro 276.00      90  Camion Grande
    ## 32      1827                  Hector Giron 456.75      90  Camion Grande
    ## 33       504      Ismael Rodero Monteagudo 126.00      30 Camion Pequeño
    ## 34      1016              Felipe Villatoro 254.00      60  Camion Grande
    ## 35       461          Angel Valdez Alegria 115.25      90          Panel
    ## 36      1368                  Hector Giron 342.00      30  Camion Grande
    ## 37      1049          Pedro Alvarez Parejo 262.25      60  Camion Grande
    ## 38       718       Fernando Mariano Berrio 179.50      60 Camion Pequeño
    ## 39      1317          Angel Valdez Alegria 329.25      90  Camion Grande
    ## 40      1945       Fernando Mariano Berrio 486.25      90  Camion Grande
    ## 41       247                  Hector Giron  61.75      30          Panel
    ## 42       980                  Hector Giron 245.00      90 Camion Pequeño
    ## 43       326 Juan Francisco Portillo Gomez  81.50      60          Panel
    ## 44      1956          Pedro Alvarez Parejo 489.00      30  Camion Grande
    ## 45       902       Fernando Mariano Berrio 225.50      60 Camion Pequeño
    ## 46      1147          Angel Valdez Alegria 286.75      60  Camion Grande
    ## 47       539             Luis Jaime Urbano 134.75      90 Camion Pequeño
    ## 48      1113          Angel Valdez Alegria 278.25      60  Camion Grande
    ## 49      1103          Pedro Alvarez Parejo 275.75      90  Camion Grande
    ## 50       303             Luis Jaime Urbano  75.75      60          Panel
    ## 51      1546       Fernando Mariano Berrio 386.50      60  Camion Grande
    ## 52       294          Pedro Alvarez Parejo  73.50      90          Panel
    ## 53      1694       Fernando Mariano Berrio 423.50      30  Camion Grande
    ## 54      1416                  Hector Giron 354.00      60  Camion Grande
    ## 55      1481        Hector Aragones Frutos 370.25      30  Camion Grande
    ## 56      1838             Luis Jaime Urbano 459.50      60  Camion Grande
    ## 57      1487             Luis Jaime Urbano 371.75      60  Camion Grande
    ## 58      1074        Hector Aragones Frutos 268.50      90  Camion Grande
    ## 59      1741        Hector Aragones Frutos 435.25      60  Camion Grande
    ## 60      1458        Hector Aragones Frutos 364.50      60  Camion Grande
    ## 61       813       Fernando Mariano Berrio 203.25      90 Camion Pequeño
    ## 62       856             Luis Jaime Urbano 214.00      60 Camion Pequeño
    ## 63       650              Felipe Villatoro 162.50      30 Camion Pequeño
    ## 64       567          Angel Valdez Alegria 141.75      30 Camion Pequeño
    ## 65      1256        Hector Aragones Frutos 314.00      30  Camion Grande
    ## 66       218             Luis Jaime Urbano  54.50      90          Panel
    ## 67       867          Pedro Alvarez Parejo 216.75      30 Camion Pequeño
    ## 68       913      Ismael Rodero Monteagudo 228.25      60 Camion Pequeño
    ## 69      1512          Angel Valdez Alegria 378.00      60  Camion Grande
    ## 70       203                  Hector Giron  50.75      90          Panel
    ## 71      1012          Angel Valdez Alegria 253.00      60  Camion Grande
    ## 72      1122        Hector Aragones Frutos 280.50      30  Camion Grande
    ## 73      1880                  Hector Giron 470.00      90  Camion Grande
    ## 74       751          Angel Valdez Alegria 187.75      60 Camion Pequeño
    ## 75      1886          Pedro Alvarez Parejo 471.50      60  Camion Grande
    ## 76       363                  Hector Giron  90.75      90          Panel
    ## 77       566 Juan Francisco Portillo Gomez 141.50      30 Camion Pequeño
    ## 78      1330              Felipe Villatoro 332.50      90  Camion Grande
    ## 79      1385 Juan Francisco Portillo Gomez 346.25      90  Camion Grande
    ## 80      1880             Luis Jaime Urbano 470.00      90  Camion Grande
    ## 81      1704          Angel Valdez Alegria 426.00      90  Camion Grande
    ## 82       214      Ismael Rodero Monteagudo  53.50      60          Panel
    ## 83       665       Fernando Mariano Berrio 166.25      60 Camion Pequeño
    ## 84      1950        Hector Aragones Frutos 487.50      90  Camion Grande
    ## 85       500          Angel Valdez Alegria 125.00      90          Panel
    ## 86       990                  Hector Giron 247.50      90 Camion Pequeño
    ## 87      1551        Hector Aragones Frutos 387.75      30  Camion Grande
    ## 88       613       Fernando Mariano Berrio 153.25      60 Camion Pequeño
    ## 89      1571       Fernando Mariano Berrio 392.75      60  Camion Grande
    ## 90       794       Fernando Mariano Berrio 198.50      60 Camion Pequeño
    ## 91      1707              Felipe Villatoro 426.75      60  Camion Grande
    ## 92      1343                  Hector Giron 335.75      60  Camion Grande
    ## 93      1022                  Hector Giron 255.50      90  Camion Grande
    ## 94       413      Ismael Rodero Monteagudo 103.25      60          Panel
    ## 95       690          Angel Valdez Alegria 172.50      90 Camion Pequeño
    ## 96       576          Pedro Alvarez Parejo 144.00      30 Camion Pequeño
    ## 97       769 Juan Francisco Portillo Gomez 192.25      60 Camion Pequeño
    ## 98       735          Pedro Alvarez Parejo 183.75      30 Camion Pequeño
    ## 99       578       Fernando Mariano Berrio 144.50      30 Camion Pequeño
    ## 100     1126 Juan Francisco Portillo Gomez 281.50      30  Camion Grande
    ## 101      907                  Hector Giron 226.75      90 Camion Pequeño
    ## 102     1842       Fernando Mariano Berrio 460.50      90  Camion Grande
    ## 103      651                  Hector Giron 162.75      90 Camion Pequeño
    ## 104      701       Fernando Mariano Berrio 175.25      90 Camion Pequeño
    ## 105      733             Luis Jaime Urbano 183.25      60 Camion Pequeño
    ## 106     1571        Hector Aragones Frutos 392.75      60  Camion Grande
    ## 107      405        Hector Aragones Frutos 101.25      30          Panel
    ## 108      872          Angel Valdez Alegria 218.00      30 Camion Pequeño
    ## 109     1167       Fernando Mariano Berrio 291.75      60  Camion Grande
    ## 110     1867      Ismael Rodero Monteagudo 466.75      60  Camion Grande
    ## 111     1975          Pedro Alvarez Parejo 493.75      30  Camion Grande
    ## 112      900      Ismael Rodero Monteagudo 225.00      60 Camion Pequeño
    ## 113     1400 Juan Francisco Portillo Gomez 350.00      30  Camion Grande
    ## 114      272          Pedro Alvarez Parejo  68.00      90          Panel
    ## 115      358 Juan Francisco Portillo Gomez  89.50      60          Panel
    ## 116     1951 Juan Francisco Portillo Gomez 487.75      60  Camion Grande
    ## 117      807        Hector Aragones Frutos 201.75      30 Camion Pequeño
    ## 118     1748          Angel Valdez Alegria 437.00      30  Camion Grande
    ## 119     1485        Hector Aragones Frutos 371.25      60  Camion Grande
    ## 120     1150      Ismael Rodero Monteagudo 287.50      60  Camion Grande
    ## 121      215          Angel Valdez Alegria  53.75      90          Panel
    ## 122      359                  Hector Giron  89.75      60          Panel
    ## 123      856       Fernando Mariano Berrio 214.00      60 Camion Pequeño
    ## 124      298          Angel Valdez Alegria  74.50      90          Panel
    ## 125      918      Ismael Rodero Monteagudo 229.50      60 Camion Pequeño
    ## 126     1093 Juan Francisco Portillo Gomez 273.25      60  Camion Grande
    ## 127     1713 Juan Francisco Portillo Gomez 428.25      30  Camion Grande
    ## 128     1763          Angel Valdez Alegria 440.75      60  Camion Grande
    ## 129     1809              Felipe Villatoro 452.25      30  Camion Grande
    ## 130     1349      Ismael Rodero Monteagudo 337.25      90  Camion Grande
    ## 131      511       Fernando Mariano Berrio 127.75      30 Camion Pequeño
    ## 132      718              Felipe Villatoro 179.50      30 Camion Pequeño
    ## 133      930              Felipe Villatoro 232.50      60 Camion Pequeño
    ## 134      272       Fernando Mariano Berrio  68.00      30          Panel
    ## 135     1804          Pedro Alvarez Parejo 451.00      30  Camion Grande
    ## 136     1373       Fernando Mariano Berrio 343.25      30  Camion Grande
    ## 137      800              Felipe Villatoro 200.00      60 Camion Pequeño
    ## 138     1638          Pedro Alvarez Parejo 409.50      60  Camion Grande
    ## 139      591          Angel Valdez Alegria 147.75      30 Camion Pequeño
    ## 140      823 Juan Francisco Portillo Gomez 205.75      90 Camion Pequeño
    ## 141     1302          Angel Valdez Alegria 325.50      30  Camion Grande
    ## 142      889          Pedro Alvarez Parejo 222.25      90 Camion Pequeño
    ## 143     1496       Fernando Mariano Berrio 374.00      60  Camion Grande
    ## 144     1394        Hector Aragones Frutos 348.50      60  Camion Grande
    ## 145     1905        Hector Aragones Frutos 476.25      90  Camion Grande
    ## 146      218             Luis Jaime Urbano  54.50      60          Panel
    ## 147     1445      Ismael Rodero Monteagudo 361.25      90  Camion Grande
    ## 148     1581      Ismael Rodero Monteagudo 395.25      90  Camion Grande
    ## 149     1407       Fernando Mariano Berrio 351.75      90  Camion Grande
    ## 150      557              Felipe Villatoro 139.25      90 Camion Pequeño
    ## 151     1636             Luis Jaime Urbano 409.00      30  Camion Grande
    ## 152     1784                  Hector Giron 446.00      60  Camion Grande
    ## 153      718        Hector Aragones Frutos 179.50      30 Camion Pequeño
    ## 154      257        Hector Aragones Frutos  64.25      60          Panel
    ## 155      425       Fernando Mariano Berrio 106.25      90          Panel
    ## 156      685        Hector Aragones Frutos 171.25      90 Camion Pequeño
    ## 157      861             Luis Jaime Urbano 215.25      60 Camion Pequeño
    ## 158     1024                  Hector Giron 256.00      30  Camion Grande
    ## 159     1180        Hector Aragones Frutos 295.00      30  Camion Grande
    ## 160     1595              Felipe Villatoro 398.75      30  Camion Grande
    ## 161      237          Angel Valdez Alegria  59.25      90          Panel
    ## 162      227             Luis Jaime Urbano  56.75      90          Panel
    ## 163     1695 Juan Francisco Portillo Gomez 423.75      30  Camion Grande
    ## 164     1666              Felipe Villatoro 416.50      90  Camion Grande
    ## 165      914                  Hector Giron 228.50      60 Camion Pequeño
    ## 166     1168              Felipe Villatoro 292.00      60  Camion Grande
    ## 167     1958      Ismael Rodero Monteagudo 489.50      60  Camion Grande
    ## 168      318       Fernando Mariano Berrio  79.50      30          Panel
    ## 169     1637 Juan Francisco Portillo Gomez 409.25      30  Camion Grande
    ## 170      923      Ismael Rodero Monteagudo 230.75      60 Camion Pequeño
    ## 171     1346             Luis Jaime Urbano 336.50      30  Camion Grande
    ## 172      817             Luis Jaime Urbano 204.25      90 Camion Pequeño
    ## 173     1948        Hector Aragones Frutos 487.00      90  Camion Grande
    ## 174     1293        Hector Aragones Frutos 323.25      30  Camion Grande
    ## 175      300        Hector Aragones Frutos  75.00      30          Panel
    ## 176     1908                  Hector Giron 477.00      30  Camion Grande
    ## 177      946             Luis Jaime Urbano 236.50      60 Camion Pequeño
    ## 178     1494       Fernando Mariano Berrio 373.50      30  Camion Grande
    ## 179      269          Angel Valdez Alegria  67.25      90          Panel
    ## 180     1608       Fernando Mariano Berrio 402.00      60  Camion Grande
    ## 181     1348             Luis Jaime Urbano 337.00      60  Camion Grande
    ## 182     1090       Fernando Mariano Berrio 272.50      60  Camion Grande
    ## 183      417              Felipe Villatoro 104.25      90          Panel
    ## 184     1748 Juan Francisco Portillo Gomez 437.00      60  Camion Grande
    ## 185      945          Angel Valdez Alegria 236.25      90 Camion Pequeño
    ## 186     1823             Luis Jaime Urbano 455.75      60  Camion Grande
    ## 187     1805              Felipe Villatoro 451.25      30  Camion Grande
    ## 188      243      Ismael Rodero Monteagudo  60.75      30          Panel
    ## 189     1198 Juan Francisco Portillo Gomez 299.50      90  Camion Grande
    ## 190      630        Hector Aragones Frutos 157.50      30 Camion Pequeño
    ## 191      218              Felipe Villatoro  54.50      90          Panel
    ## 192      239          Pedro Alvarez Parejo  59.75      30          Panel
    ## 193     1585      Ismael Rodero Monteagudo 396.25      30  Camion Grande
    ## 194     1640        Hector Aragones Frutos 410.00      60  Camion Grande
    ## 195      723                  Hector Giron 180.75      30 Camion Pequeño
    ## 196      766      Ismael Rodero Monteagudo 191.50      90 Camion Pequeño
    ##     mes anio
    ## 1    04 2018
    ## 2    04 2018
    ## 3    04 2018
    ## 4    04 2018
    ## 5    04 2018
    ## 6    04 2018
    ## 7    04 2018
    ## 8    04 2018
    ## 9    04 2018
    ## 10   04 2018
    ## 11   04 2018
    ## 12   04 2018
    ## 13   04 2018
    ## 14   04 2018
    ## 15   04 2018
    ## 16   04 2018
    ## 17   04 2018
    ## 18   04 2018
    ## 19   04 2018
    ## 20   04 2018
    ## 21   04 2018
    ## 22   04 2018
    ## 23   04 2018
    ## 24   04 2018
    ## 25   04 2018
    ## 26   04 2018
    ## 27   04 2018
    ## 28   04 2018
    ## 29   04 2018
    ## 30   04 2018
    ## 31   04 2018
    ## 32   04 2018
    ## 33   04 2018
    ## 34   04 2018
    ## 35   04 2018
    ## 36   04 2018
    ## 37   04 2018
    ## 38   04 2018
    ## 39   04 2018
    ## 40   04 2018
    ## 41   04 2018
    ## 42   04 2018
    ## 43   04 2018
    ## 44   04 2018
    ## 45   04 2018
    ## 46   04 2018
    ## 47   04 2018
    ## 48   04 2018
    ## 49   04 2018
    ## 50   04 2018
    ## 51   04 2018
    ## 52   04 2018
    ## 53   04 2018
    ## 54   04 2018
    ## 55   04 2018
    ## 56   04 2018
    ## 57   04 2018
    ## 58   04 2018
    ## 59   04 2018
    ## 60   04 2018
    ## 61   04 2018
    ## 62   04 2018
    ## 63   04 2018
    ## 64   04 2018
    ## 65   04 2018
    ## 66   04 2018
    ## 67   04 2018
    ## 68   04 2018
    ## 69   04 2018
    ## 70   04 2018
    ## 71   04 2018
    ## 72   04 2018
    ## 73   04 2018
    ## 74   04 2018
    ## 75   04 2018
    ## 76   04 2018
    ## 77   04 2018
    ## 78   04 2018
    ## 79   04 2018
    ## 80   04 2018
    ## 81   04 2018
    ## 82   04 2018
    ## 83   04 2018
    ## 84   04 2018
    ## 85   04 2018
    ## 86   04 2018
    ## 87   04 2018
    ## 88   04 2018
    ## 89   04 2018
    ## 90   04 2018
    ## 91   04 2018
    ## 92   04 2018
    ## 93   04 2018
    ## 94   04 2018
    ## 95   04 2018
    ## 96   04 2018
    ## 97   04 2018
    ## 98   04 2018
    ## 99   04 2018
    ## 100  04 2018
    ## 101  04 2018
    ## 102  04 2018
    ## 103  04 2018
    ## 104  04 2018
    ## 105  04 2018
    ## 106  04 2018
    ## 107  04 2018
    ## 108  04 2018
    ## 109  04 2018
    ## 110  04 2018
    ## 111  04 2018
    ## 112  04 2018
    ## 113  04 2018
    ## 114  04 2018
    ## 115  04 2018
    ## 116  04 2018
    ## 117  04 2018
    ## 118  04 2018
    ## 119  04 2018
    ## 120  04 2018
    ## 121  04 2018
    ## 122  04 2018
    ## 123  04 2018
    ## 124  04 2018
    ## 125  04 2018
    ## 126  04 2018
    ## 127  04 2018
    ## 128  04 2018
    ## 129  04 2018
    ## 130  04 2018
    ## 131  04 2018
    ## 132  04 2018
    ## 133  04 2018
    ## 134  04 2018
    ## 135  04 2018
    ## 136  04 2018
    ## 137  04 2018
    ## 138  04 2018
    ## 139  04 2018
    ## 140  04 2018
    ## 141  04 2018
    ## 142  04 2018
    ## 143  04 2018
    ## 144  04 2018
    ## 145  04 2018
    ## 146  04 2018
    ## 147  04 2018
    ## 148  04 2018
    ## 149  04 2018
    ## 150  04 2018
    ## 151  04 2018
    ## 152  04 2018
    ## 153  04 2018
    ## 154  04 2018
    ## 155  04 2018
    ## 156  04 2018
    ## 157  04 2018
    ## 158  04 2018
    ## 159  04 2018
    ## 160  04 2018
    ## 161  04 2018
    ## 162  04 2018
    ## 163  04 2018
    ## 164  04 2018
    ## 165  04 2018
    ## 166  04 2018
    ## 167  04 2018
    ## 168  04 2018
    ## 169  04 2018
    ## 170  04 2018
    ## 171  04 2018
    ## 172  04 2018
    ## 173  04 2018
    ## 174  04 2018
    ## 175  04 2018
    ## 176  04 2018
    ## 177  04 2018
    ## 178  04 2018
    ## 179  04 2018
    ## 180  04 2018
    ## 181  04 2018
    ## 182  04 2018
    ## 183  04 2018
    ## 184  04 2018
    ## 185  04 2018
    ## 186  04 2018
    ## 187  04 2018
    ## 188  04 2018
    ## 189  04 2018
    ## 190  04 2018
    ## 191  04 2018
    ## 192  04 2018
    ## 193  04 2018
    ## 194  04 2018
    ## 195  04 2018
    ## 196  04 2018
    ## 
    ## [[5]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10000774                                     BAR LA OFICINA     76001
    ## 2    10000775                     EL PINCHE OBELISCO |||Faltante     76001
    ## 3    10000776            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 4    10000777                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 5    10000778      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 6    10000779        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 7    10000780                EL GALLO NEGRO / Despacho a cliente     76002
    ## 8    10000781                                        UBIQUO LABS     76001
    ## 9    10000782                            UBIQUO LABS |||FALTANTE     76001
    ## 10   10000783                  POLLO PINULITO/Despacho a cliente     76002
    ## 11   10000784            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 12   10000785                EL GALLO NEGRO / Despacho a cliente     76001
    ## 13   10000786                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 14   10000787        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 15   10000788                              HOSPITAL LAS AMERICAS     76002
    ## 16   10000789                            UBIQUO LABS |||FALTANTE     76001
    ## 17   10000790                  POLLO PINULITO/Despacho a cliente     76002
    ## 18   10000791 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 19   10000792                              HOSPITAL LAS AMERICAS     76001
    ## 20   10000793           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 21   10000794                            UBIQUO LABS |||FALTANTE     76001
    ## 22   10000795                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 23   10000796                              HOSPITAL LAS AMERICAS     76002
    ## 24   10000797                              HOSPITAL LAS AMERICAS     76001
    ## 25   10000798           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 26   10000799                EL GALLO NEGRO / Despacho a cliente     76002
    ## 27   10000800                EL GALLO NEGRO / Despacho a cliente     76002
    ## 28   10000801                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 29   10000802                EL GALLO NEGRO / Despacho a cliente     76002
    ## 30   10000803           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 31   10000804                                TAQUERIA EL CHINITO     76002
    ## 32   10000805 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 33   10000806                            UBIQUO LABS |||FALTANTE     76002
    ## 34   10000807                              HOSPITAL LAS AMERICAS     76002
    ## 35   10000808           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 36   10000809                EL GALLO NEGRO / Despacho a cliente     76001
    ## 37   10000810            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 38   10000811                                TAQUERIA EL CHINITO     76001
    ## 39   10000812                     EL PINCHE OBELISCO |||Faltante     76001
    ## 40   10000813                                     BAR LA OFICINA     76002
    ## 41   10000814           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 42   10000815                EL GALLO NEGRO / Despacho a cliente     76002
    ## 43   10000816                  POLLO PINULITO/Despacho a cliente     76002
    ## 44   10000817                EL GALLO NEGRO / Despacho a cliente     76001
    ## 45   10000818      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 46   10000819        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 47   10000820                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 48   10000821                     EL PINCHE OBELISCO |||Faltante     76001
    ## 49   10000822           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 50   10000823                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 51   10000824                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 52   10000825                                TAQUERIA EL CHINITO     76002
    ## 53   10000826 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 54   10000827           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 55   10000828                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 56   10000829                  POLLO PINULITO/Despacho a cliente     76002
    ## 57   10000830            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 58   10000831                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 59   10000832      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 60   10000833                     EL PINCHE OBELISCO |||Faltante     76001
    ## 61   10000834                            UBIQUO LABS |||FALTANTE     76001
    ## 62   10000835      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 63   10000836           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 64   10000837                     EL PINCHE OBELISCO |||Faltante     76001
    ## 65   10000838                                TAQUERIA EL CHINITO     76001
    ## 66   10000839                EL GALLO NEGRO / Despacho a cliente     76001
    ## 67   10000840      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 68   10000841                                     BAR LA OFICINA     76001
    ## 69   10000842                            UBIQUO LABS |||FALTANTE     76002
    ## 70   10000843                                        UBIQUO LABS     76002
    ## 71   10000844            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 72   10000845        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 73   10000846                     EL PINCHE OBELISCO |||Faltante     76001
    ## 74   10000847                     EL PINCHE OBELISCO |||Faltante     76001
    ## 75   10000848                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 76   10000849           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 77   10000850      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 78   10000851           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 79   10000852                                        UBIQUO LABS     76001
    ## 80   10000853                              HOSPITAL LAS AMERICAS     76002
    ## 81   10000854            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 82   10000855 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 83   10000856      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 84   10000857        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 85   10000858            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 86   10000859                          POLLO PINULITO|||FALTANTE     76001
    ## 87   10000860      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 88   10000861                     EL PINCHE OBELISCO |||Faltante     76002
    ## 89   10000862        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 90   10000863                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 91   10000864                     EL PINCHE OBELISCO |||Faltante     76002
    ## 92   10000865                EL GALLO NEGRO / Despacho a cliente     76001
    ## 93   10000866 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 94   10000867                EL GALLO NEGRO / Despacho a cliente     76001
    ## 95   10000868           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 96   10000869            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 97   10000870        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 98   10000871                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 99   10000872            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 100  10000873           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 101  10000874                                TAQUERIA EL CHINITO     76002
    ## 102  10000875                                        UBIQUO LABS     76001
    ## 103  10000876                                        UBIQUO LABS     76002
    ## 104  10000877                          POLLO PINULITO|||FALTANTE     76001
    ## 105  10000878                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 106  10000879                            UBIQUO LABS |||FALTANTE     76001
    ## 107  10000880            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 108  10000881                                        UBIQUO LABS     76001
    ## 109  10000882                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 110  10000883                                        UBIQUO LABS     76002
    ## 111  10000884                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 112  10000885 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 113  10000886                                        UBIQUO LABS     76002
    ## 114  10000887                                     BAR LA OFICINA     76001
    ## 115  10000888                          POLLO PINULITO|||FALTANTE     76002
    ## 116  10000889                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 117  10000890            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 118  10000891                                TAQUERIA EL CHINITO     76001
    ## 119  10000892                                TAQUERIA EL CHINITO     76002
    ## 120  10000893                          POLLO PINULITO|||FALTANTE     76002
    ## 121  10000894           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 122  10000895                                TAQUERIA EL CHINITO     76001
    ## 123  10000896        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 124  10000897                            UBIQUO LABS |||FALTANTE     76002
    ## 125  10000898                            UBIQUO LABS |||FALTANTE     76001
    ## 126  10000899                     EL PINCHE OBELISCO |||Faltante     76002
    ## 127  10000900 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 128  10000901      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 129  10000902 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 130  10000903      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 131  10000904                            UBIQUO LABS |||FALTANTE     76002
    ## 132  10000905 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 133  10000906                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 134  10000907            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 135  10000908                                TAQUERIA EL CHINITO     76002
    ## 136  10000909            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 137  10000910                EL GALLO NEGRO / Despacho a cliente     76002
    ## 138  10000911                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 139  10000912                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 140  10000913                                     BAR LA OFICINA     76002
    ## 141  10000914                              HOSPITAL LAS AMERICAS     76001
    ## 142  10000915                                TAQUERIA EL CHINITO     76001
    ## 143  10000916                  POLLO PINULITO/Despacho a cliente     76002
    ## 144  10000917                  POLLO PINULITO/Despacho a cliente     76001
    ## 145  10000918 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 146  10000919                                TAQUERIA EL CHINITO     76001
    ## 147  10000920                          POLLO PINULITO|||FALTANTE     76002
    ## 148  10000921 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 149  10000922      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 150  10000923                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 151  10000924                                     BAR LA OFICINA     76002
    ## 152  10000925            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 153  10000926           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 154  10000927           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 155  10000928            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 156  10000929                  POLLO PINULITO/Despacho a cliente     76002
    ## 157  10000930                                        UBIQUO LABS     76002
    ## 158  10000931           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 159  10000932            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 160  10000933                                TAQUERIA EL CHINITO     76002
    ## 161  10000934                     EL PINCHE OBELISCO |||Faltante     76001
    ## 162  10000935           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 163  10000936                     EL PINCHE OBELISCO |||Faltante     76002
    ## 164  10000937           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 165  10000938                              HOSPITAL LAS AMERICAS     76001
    ## 166  10000939        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 167  10000940                                     BAR LA OFICINA     76002
    ## 168  10000941 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 169  10000942                                     BAR LA OFICINA     76001
    ## 170  10000943                                TAQUERIA EL CHINITO     76001
    ## 171  10000944           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 172  10000945 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 173  10000946 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 174  10000947            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 175  10000948                                TAQUERIA EL CHINITO     76001
    ## 176  10000949                              HOSPITAL LAS AMERICAS     76001
    ## 177  10000950                                        UBIQUO LABS     76001
    ## 178  10000951      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 179  10000952                              HOSPITAL LAS AMERICAS     76001
    ## 180  10000953                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 181  10000954           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 182  10000955                                TAQUERIA EL CHINITO     76002
    ## 183  10000956                  POLLO PINULITO/Despacho a cliente     76001
    ## 184  10000957 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 185  10000958                                TAQUERIA EL CHINITO     76002
    ## 186  10000959        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 187  10000960                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 188  10000961            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 189  10000962                            UBIQUO LABS |||FALTANTE     76002
    ## 190  10000963                                        UBIQUO LABS     76002
    ## 191  10000964                                        UBIQUO LABS     76002
    ## 192  10000965                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 193  10000966 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 194  10000967                                     BAR LA OFICINA     76002
    ## 195  10000968                              HOSPITAL LAS AMERICAS     76002
    ## 196  10000969                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 197  10000970                            UBIQUO LABS |||FALTANTE     76001
    ## 198  10000971                     EL PINCHE OBELISCO |||Faltante     76002
    ## 199  10000972 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 200  10000973                EL GALLO NEGRO / Despacho a cliente     76001
    ## 201  10000974 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 202  10000975                                TAQUERIA EL CHINITO     76002
    ## 203  10000976           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 204  10000977                EL GALLO NEGRO / Despacho a cliente     76001
    ## 205  10000978                                     BAR LA OFICINA     76001
    ## 206  10000979                          POLLO PINULITO|||FALTANTE     76002
    ## 207  10000980                                TAQUERIA EL CHINITO     76002
    ## 208  10000981                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 209  10000982                                        UBIQUO LABS     76002
    ## 210  10000983            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 211  10000984                                        UBIQUO LABS     76001
    ## 212  10000985                  POLLO PINULITO/Despacho a cliente     76002
    ## 213  10000986                          POLLO PINULITO|||FALTANTE     76002
    ## 214  10000987 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 215  10000988                       EL GALLO NEGRO |||DEVOLUCION     76002
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1        509             Luis Jaime Urbano 127.25      30 Camion Pequeño
    ## 2        243       Fernando Mariano Berrio  60.75      30          Panel
    ## 3       1513      Ismael Rodero Monteagudo 378.25      60  Camion Grande
    ## 4        287             Luis Jaime Urbano  71.75      60          Panel
    ## 5       1764          Angel Valdez Alegria 441.00      90  Camion Grande
    ## 6       1669 Juan Francisco Portillo Gomez 417.25      90  Camion Grande
    ## 7        954        Hector Aragones Frutos 238.50      30 Camion Pequeño
    ## 8        679 Juan Francisco Portillo Gomez 169.75      30 Camion Pequeño
    ## 9        267                  Hector Giron  66.75      90          Panel
    ## 10       922             Luis Jaime Urbano 230.50      60 Camion Pequeño
    ## 11       938        Hector Aragones Frutos 234.50      90 Camion Pequeño
    ## 12      1822 Juan Francisco Portillo Gomez 455.50      90  Camion Grande
    ## 13       711       Fernando Mariano Berrio 177.75      60 Camion Pequeño
    ## 14      1829        Hector Aragones Frutos 457.25      30  Camion Grande
    ## 15       323                  Hector Giron  80.75      60          Panel
    ## 16       559                  Hector Giron 139.75      60 Camion Pequeño
    ## 17      1847          Angel Valdez Alegria 461.75      60  Camion Grande
    ## 18      1735             Luis Jaime Urbano 433.75      30  Camion Grande
    ## 19      1811 Juan Francisco Portillo Gomez 452.75      90  Camion Grande
    ## 20      1381             Luis Jaime Urbano 345.25      30  Camion Grande
    ## 21      1879        Hector Aragones Frutos 469.75      90  Camion Grande
    ## 22      1914             Luis Jaime Urbano 478.50      60  Camion Grande
    ## 23      1490          Angel Valdez Alegria 372.50      60  Camion Grande
    ## 24       465        Hector Aragones Frutos 116.25      90          Panel
    ## 25       279                  Hector Giron  69.75      30          Panel
    ## 26       310             Luis Jaime Urbano  77.50      30          Panel
    ## 27      1439              Felipe Villatoro 359.75      30  Camion Grande
    ## 28      1387        Hector Aragones Frutos 346.75      30  Camion Grande
    ## 29      1596             Luis Jaime Urbano 399.00      30  Camion Grande
    ## 30      1074          Pedro Alvarez Parejo 268.50      90  Camion Grande
    ## 31       505          Angel Valdez Alegria 126.25      30 Camion Pequeño
    ## 32      1662          Pedro Alvarez Parejo 415.50      30  Camion Grande
    ## 33       757       Fernando Mariano Berrio 189.25      90 Camion Pequeño
    ## 34      1991      Ismael Rodero Monteagudo 497.75      30  Camion Grande
    ## 35       231 Juan Francisco Portillo Gomez  57.75      90          Panel
    ## 36       959                  Hector Giron 239.75      90 Camion Pequeño
    ## 37       382       Fernando Mariano Berrio  95.50      60          Panel
    ## 38       736              Felipe Villatoro 184.00      90 Camion Pequeño
    ## 39      1734      Ismael Rodero Monteagudo 433.50      90  Camion Grande
    ## 40       584       Fernando Mariano Berrio 146.00      30 Camion Pequeño
    ## 41       524                  Hector Giron 131.00      90 Camion Pequeño
    ## 42       598                  Hector Giron 149.50      30 Camion Pequeño
    ## 43       851                  Hector Giron 212.75      60 Camion Pequeño
    ## 44      1621        Hector Aragones Frutos 405.25      30  Camion Grande
    ## 45       659          Angel Valdez Alegria 164.75      60 Camion Pequeño
    ## 46       810          Angel Valdez Alegria 202.50      90 Camion Pequeño
    ## 47       937             Luis Jaime Urbano 234.25      90 Camion Pequeño
    ## 48      1884      Ismael Rodero Monteagudo 471.00      60  Camion Grande
    ## 49       689 Juan Francisco Portillo Gomez 172.25      90 Camion Pequeño
    ## 50      1754      Ismael Rodero Monteagudo 438.50      30  Camion Grande
    ## 51      1705      Ismael Rodero Monteagudo 426.25      90  Camion Grande
    ## 52      1100      Ismael Rodero Monteagudo 275.00      60  Camion Grande
    ## 53       899          Angel Valdez Alegria 224.75      30 Camion Pequeño
    ## 54       953          Angel Valdez Alegria 238.25      90 Camion Pequeño
    ## 55      1262             Luis Jaime Urbano 315.50      60  Camion Grande
    ## 56      1496      Ismael Rodero Monteagudo 374.00      90  Camion Grande
    ## 57       810       Fernando Mariano Berrio 202.50      30 Camion Pequeño
    ## 58      1821       Fernando Mariano Berrio 455.25      90  Camion Grande
    ## 59       563          Angel Valdez Alegria 140.75      60 Camion Pequeño
    ## 60      1378 Juan Francisco Portillo Gomez 344.50      90  Camion Grande
    ## 61       561 Juan Francisco Portillo Gomez 140.25      60 Camion Pequeño
    ## 62      1349                  Hector Giron 337.25      30  Camion Grande
    ## 63      1047       Fernando Mariano Berrio 261.75      60  Camion Grande
    ## 64      1219              Felipe Villatoro 304.75      90  Camion Grande
    ## 65       591              Felipe Villatoro 147.75      60 Camion Pequeño
    ## 66       980      Ismael Rodero Monteagudo 245.00      60 Camion Pequeño
    ## 67       537       Fernando Mariano Berrio 134.25      60 Camion Pequeño
    ## 68       395 Juan Francisco Portillo Gomez  98.75      30          Panel
    ## 69      1396        Hector Aragones Frutos 349.00      60  Camion Grande
    ## 70      1559        Hector Aragones Frutos 389.75      60  Camion Grande
    ## 71      1116             Luis Jaime Urbano 279.00      30  Camion Grande
    ## 72      1507        Hector Aragones Frutos 376.75      60  Camion Grande
    ## 73       752       Fernando Mariano Berrio 188.00      90 Camion Pequeño
    ## 74      1938                  Hector Giron 484.50      60  Camion Grande
    ## 75      1823       Fernando Mariano Berrio 455.75      90  Camion Grande
    ## 76      1740       Fernando Mariano Berrio 435.00      60  Camion Grande
    ## 77       937                  Hector Giron 234.25      90 Camion Pequeño
    ## 78      1842          Pedro Alvarez Parejo 460.50      90  Camion Grande
    ## 79      1090       Fernando Mariano Berrio 272.50      60  Camion Grande
    ## 80      1342      Ismael Rodero Monteagudo 335.50      60  Camion Grande
    ## 81      1618       Fernando Mariano Berrio 404.50      90  Camion Grande
    ## 82      1753          Pedro Alvarez Parejo 438.25      30  Camion Grande
    ## 83       681             Luis Jaime Urbano 170.25      30 Camion Pequeño
    ## 84      1908             Luis Jaime Urbano 477.00      90  Camion Grande
    ## 85       340             Luis Jaime Urbano  85.00      30          Panel
    ## 86      1902       Fernando Mariano Berrio 475.50      60  Camion Grande
    ## 87      1949        Hector Aragones Frutos 487.25      30  Camion Grande
    ## 88      1583      Ismael Rodero Monteagudo 395.75      30  Camion Grande
    ## 89      1713      Ismael Rodero Monteagudo 428.25      30  Camion Grande
    ## 90      1454             Luis Jaime Urbano 363.50      60  Camion Grande
    ## 91       469       Fernando Mariano Berrio 117.25      60          Panel
    ## 92       620              Felipe Villatoro 155.00      90 Camion Pequeño
    ## 93      1169       Fernando Mariano Berrio 292.25      30  Camion Grande
    ## 94      1619        Hector Aragones Frutos 404.75      30  Camion Grande
    ## 95       880 Juan Francisco Portillo Gomez 220.00      30 Camion Pequeño
    ## 96      1623          Pedro Alvarez Parejo 405.75      90  Camion Grande
    ## 97      1079        Hector Aragones Frutos 269.75      60  Camion Grande
    ## 98       582              Felipe Villatoro 145.50      60 Camion Pequeño
    ## 99      1882       Fernando Mariano Berrio 470.50      60  Camion Grande
    ## 100     1330             Luis Jaime Urbano 332.50      60  Camion Grande
    ## 101      751        Hector Aragones Frutos 187.75      90 Camion Pequeño
    ## 102     1697 Juan Francisco Portillo Gomez 424.25      30  Camion Grande
    ## 103     1261 Juan Francisco Portillo Gomez 315.25      60  Camion Grande
    ## 104     1722             Luis Jaime Urbano 430.50      30  Camion Grande
    ## 105      639      Ismael Rodero Monteagudo 159.75      60 Camion Pequeño
    ## 106      504        Hector Aragones Frutos 126.00      60 Camion Pequeño
    ## 107     1400             Luis Jaime Urbano 350.00      30  Camion Grande
    ## 108     1132      Ismael Rodero Monteagudo 283.00      60  Camion Grande
    ## 109      331             Luis Jaime Urbano  82.75      60          Panel
    ## 110     1064      Ismael Rodero Monteagudo 266.00      30  Camion Grande
    ## 111     1455       Fernando Mariano Berrio 363.75      30  Camion Grande
    ## 112      925          Angel Valdez Alegria 231.25      30 Camion Pequeño
    ## 113      683          Pedro Alvarez Parejo 170.75      60 Camion Pequeño
    ## 114      370 Juan Francisco Portillo Gomez  92.50      30          Panel
    ## 115      510              Felipe Villatoro 127.50      30 Camion Pequeño
    ## 116      875       Fernando Mariano Berrio 218.75      60 Camion Pequeño
    ## 117      271                  Hector Giron  67.75      60          Panel
    ## 118     1522              Felipe Villatoro 380.50      30  Camion Grande
    ## 119     1082             Luis Jaime Urbano 270.50      30  Camion Grande
    ## 120      966          Angel Valdez Alegria 241.50      90 Camion Pequeño
    ## 121     1150          Angel Valdez Alegria 287.50      30  Camion Grande
    ## 122     1887              Felipe Villatoro 471.75      90  Camion Grande
    ## 123      714              Felipe Villatoro 178.50      90 Camion Pequeño
    ## 124     1340        Hector Aragones Frutos 335.00      30  Camion Grande
    ## 125     1289                  Hector Giron 322.25      60  Camion Grande
    ## 126      807          Pedro Alvarez Parejo 201.75      60 Camion Pequeño
    ## 127     1833        Hector Aragones Frutos 458.25      90  Camion Grande
    ## 128     1301       Fernando Mariano Berrio 325.25      60  Camion Grande
    ## 129      651          Pedro Alvarez Parejo 162.75      60 Camion Pequeño
    ## 130      225          Pedro Alvarez Parejo  56.25      90          Panel
    ## 131      935 Juan Francisco Portillo Gomez 233.75      90 Camion Pequeño
    ## 132      840                  Hector Giron 210.00      60 Camion Pequeño
    ## 133      820             Luis Jaime Urbano 205.00      90 Camion Pequeño
    ## 134      587 Juan Francisco Portillo Gomez 146.75      30 Camion Pequeño
    ## 135      581             Luis Jaime Urbano 145.25      60 Camion Pequeño
    ## 136     1769             Luis Jaime Urbano 442.25      30  Camion Grande
    ## 137      847       Fernando Mariano Berrio 211.75      30 Camion Pequeño
    ## 138     1168      Ismael Rodero Monteagudo 292.00      60  Camion Grande
    ## 139     1760 Juan Francisco Portillo Gomez 440.00      90  Camion Grande
    ## 140     1877                  Hector Giron 469.25      60  Camion Grande
    ## 141     1132       Fernando Mariano Berrio 283.00      90  Camion Grande
    ## 142     1187             Luis Jaime Urbano 296.75      90  Camion Grande
    ## 143      472              Felipe Villatoro 118.00      30          Panel
    ## 144     1774      Ismael Rodero Monteagudo 443.50      60  Camion Grande
    ## 145      362                  Hector Giron  90.50      60          Panel
    ## 146     1310              Felipe Villatoro 327.50      60  Camion Grande
    ## 147      885              Felipe Villatoro 221.25      60 Camion Pequeño
    ## 148     1920 Juan Francisco Portillo Gomez 480.00      30  Camion Grande
    ## 149      319              Felipe Villatoro  79.75      30          Panel
    ## 150      202        Hector Aragones Frutos  50.50      60          Panel
    ## 151      504             Luis Jaime Urbano 126.00      30 Camion Pequeño
    ## 152     1167      Ismael Rodero Monteagudo 291.75      30  Camion Grande
    ## 153     1755      Ismael Rodero Monteagudo 438.75      60  Camion Grande
    ## 154      489        Hector Aragones Frutos 122.25      90          Panel
    ## 155      299          Angel Valdez Alegria  74.75      60          Panel
    ## 156     1754                  Hector Giron 438.50      90  Camion Grande
    ## 157      810 Juan Francisco Portillo Gomez 202.50      30 Camion Pequeño
    ## 158     1805      Ismael Rodero Monteagudo 451.25      90  Camion Grande
    ## 159     1980       Fernando Mariano Berrio 495.00      90  Camion Grande
    ## 160      942              Felipe Villatoro 235.50      30 Camion Pequeño
    ## 161     1810       Fernando Mariano Berrio 452.50      90  Camion Grande
    ## 162      916          Angel Valdez Alegria 229.00      60 Camion Pequeño
    ## 163      681                  Hector Giron 170.25      30 Camion Pequeño
    ## 164     1028          Pedro Alvarez Parejo 257.00      90  Camion Grande
    ## 165     1818          Pedro Alvarez Parejo 454.50      90  Camion Grande
    ## 166      813        Hector Aragones Frutos 203.25      30 Camion Pequeño
    ## 167      575          Angel Valdez Alegria 143.75      60 Camion Pequeño
    ## 168     1296                  Hector Giron 324.00      60  Camion Grande
    ## 169     1023          Pedro Alvarez Parejo 255.75      30  Camion Grande
    ## 170     1333             Luis Jaime Urbano 333.25      90  Camion Grande
    ## 171      560 Juan Francisco Portillo Gomez 140.00      60 Camion Pequeño
    ## 172      719                  Hector Giron 179.75      60 Camion Pequeño
    ## 173     1442       Fernando Mariano Berrio 360.50      60  Camion Grande
    ## 174     1430       Fernando Mariano Berrio 357.50      60  Camion Grande
    ## 175     1201        Hector Aragones Frutos 300.25      60  Camion Grande
    ## 176     1212 Juan Francisco Portillo Gomez 303.00      30  Camion Grande
    ## 177      310             Luis Jaime Urbano  77.50      60          Panel
    ## 178     1057          Pedro Alvarez Parejo 264.25      90  Camion Grande
    ## 179      971          Angel Valdez Alegria 242.75      60 Camion Pequeño
    ## 180     1006          Pedro Alvarez Parejo 251.50      30  Camion Grande
    ## 181     1005 Juan Francisco Portillo Gomez 251.25      30  Camion Grande
    ## 182      470 Juan Francisco Portillo Gomez 117.50      60          Panel
    ## 183     1641                  Hector Giron 410.25      90  Camion Grande
    ## 184      890          Angel Valdez Alegria 222.50      60 Camion Pequeño
    ## 185     1392       Fernando Mariano Berrio 348.00      90  Camion Grande
    ## 186     1317          Pedro Alvarez Parejo 329.25      30  Camion Grande
    ## 187     1802        Hector Aragones Frutos 450.50      30  Camion Grande
    ## 188      870       Fernando Mariano Berrio 217.50      90 Camion Pequeño
    ## 189     1497          Angel Valdez Alegria 374.25      30  Camion Grande
    ## 190      736                  Hector Giron 184.00      60 Camion Pequeño
    ## 191      767             Luis Jaime Urbano 191.75      60 Camion Pequeño
    ## 192     1371          Angel Valdez Alegria 342.75      90  Camion Grande
    ## 193     1211          Angel Valdez Alegria 302.75      30  Camion Grande
    ## 194     1816 Juan Francisco Portillo Gomez 454.00      90  Camion Grande
    ## 195     1726       Fernando Mariano Berrio 431.50      90  Camion Grande
    ## 196      801          Angel Valdez Alegria 200.25      90 Camion Pequeño
    ## 197     1512 Juan Francisco Portillo Gomez 378.00      30  Camion Grande
    ## 198      633                  Hector Giron 158.25      60 Camion Pequeño
    ## 199      933          Pedro Alvarez Parejo 233.25      60 Camion Pequeño
    ## 200     1657       Fernando Mariano Berrio 414.25      30  Camion Grande
    ## 201      234          Angel Valdez Alegria  58.50      90          Panel
    ## 202      203             Luis Jaime Urbano  50.75      30          Panel
    ## 203     1848          Angel Valdez Alegria 462.00      30  Camion Grande
    ## 204     1307        Hector Aragones Frutos 326.75      60  Camion Grande
    ## 205     1139        Hector Aragones Frutos 284.75      90  Camion Grande
    ## 206      784       Fernando Mariano Berrio 196.00      60 Camion Pequeño
    ## 207     1825             Luis Jaime Urbano 456.25      60  Camion Grande
    ## 208      682              Felipe Villatoro 170.50      60 Camion Pequeño
    ## 209      735             Luis Jaime Urbano 183.75      60 Camion Pequeño
    ## 210     1062              Felipe Villatoro 265.50      60  Camion Grande
    ## 211     1733              Felipe Villatoro 433.25      90  Camion Grande
    ## 212     1483                  Hector Giron 370.75      30  Camion Grande
    ## 213     1311                  Hector Giron 327.75      60  Camion Grande
    ## 214      933        Hector Aragones Frutos 233.25      60 Camion Pequeño
    ## 215     1838             Luis Jaime Urbano 459.50      90  Camion Grande
    ##     mes anio
    ## 1    05 2018
    ## 2    05 2018
    ## 3    05 2018
    ## 4    05 2018
    ## 5    05 2018
    ## 6    05 2018
    ## 7    05 2018
    ## 8    05 2018
    ## 9    05 2018
    ## 10   05 2018
    ## 11   05 2018
    ## 12   05 2018
    ## 13   05 2018
    ## 14   05 2018
    ## 15   05 2018
    ## 16   05 2018
    ## 17   05 2018
    ## 18   05 2018
    ## 19   05 2018
    ## 20   05 2018
    ## 21   05 2018
    ## 22   05 2018
    ## 23   05 2018
    ## 24   05 2018
    ## 25   05 2018
    ## 26   05 2018
    ## 27   05 2018
    ## 28   05 2018
    ## 29   05 2018
    ## 30   05 2018
    ## 31   05 2018
    ## 32   05 2018
    ## 33   05 2018
    ## 34   05 2018
    ## 35   05 2018
    ## 36   05 2018
    ## 37   05 2018
    ## 38   05 2018
    ## 39   05 2018
    ## 40   05 2018
    ## 41   05 2018
    ## 42   05 2018
    ## 43   05 2018
    ## 44   05 2018
    ## 45   05 2018
    ## 46   05 2018
    ## 47   05 2018
    ## 48   05 2018
    ## 49   05 2018
    ## 50   05 2018
    ## 51   05 2018
    ## 52   05 2018
    ## 53   05 2018
    ## 54   05 2018
    ## 55   05 2018
    ## 56   05 2018
    ## 57   05 2018
    ## 58   05 2018
    ## 59   05 2018
    ## 60   05 2018
    ## 61   05 2018
    ## 62   05 2018
    ## 63   05 2018
    ## 64   05 2018
    ## 65   05 2018
    ## 66   05 2018
    ## 67   05 2018
    ## 68   05 2018
    ## 69   05 2018
    ## 70   05 2018
    ## 71   05 2018
    ## 72   05 2018
    ## 73   05 2018
    ## 74   05 2018
    ## 75   05 2018
    ## 76   05 2018
    ## 77   05 2018
    ## 78   05 2018
    ## 79   05 2018
    ## 80   05 2018
    ## 81   05 2018
    ## 82   05 2018
    ## 83   05 2018
    ## 84   05 2018
    ## 85   05 2018
    ## 86   05 2018
    ## 87   05 2018
    ## 88   05 2018
    ## 89   05 2018
    ## 90   05 2018
    ## 91   05 2018
    ## 92   05 2018
    ## 93   05 2018
    ## 94   05 2018
    ## 95   05 2018
    ## 96   05 2018
    ## 97   05 2018
    ## 98   05 2018
    ## 99   05 2018
    ## 100  05 2018
    ## 101  05 2018
    ## 102  05 2018
    ## 103  05 2018
    ## 104  05 2018
    ## 105  05 2018
    ## 106  05 2018
    ## 107  05 2018
    ## 108  05 2018
    ## 109  05 2018
    ## 110  05 2018
    ## 111  05 2018
    ## 112  05 2018
    ## 113  05 2018
    ## 114  05 2018
    ## 115  05 2018
    ## 116  05 2018
    ## 117  05 2018
    ## 118  05 2018
    ## 119  05 2018
    ## 120  05 2018
    ## 121  05 2018
    ## 122  05 2018
    ## 123  05 2018
    ## 124  05 2018
    ## 125  05 2018
    ## 126  05 2018
    ## 127  05 2018
    ## 128  05 2018
    ## 129  05 2018
    ## 130  05 2018
    ## 131  05 2018
    ## 132  05 2018
    ## 133  05 2018
    ## 134  05 2018
    ## 135  05 2018
    ## 136  05 2018
    ## 137  05 2018
    ## 138  05 2018
    ## 139  05 2018
    ## 140  05 2018
    ## 141  05 2018
    ## 142  05 2018
    ## 143  05 2018
    ## 144  05 2018
    ## 145  05 2018
    ## 146  05 2018
    ## 147  05 2018
    ## 148  05 2018
    ## 149  05 2018
    ## 150  05 2018
    ## 151  05 2018
    ## 152  05 2018
    ## 153  05 2018
    ## 154  05 2018
    ## 155  05 2018
    ## 156  05 2018
    ## 157  05 2018
    ## 158  05 2018
    ## 159  05 2018
    ## 160  05 2018
    ## 161  05 2018
    ## 162  05 2018
    ## 163  05 2018
    ## 164  05 2018
    ## 165  05 2018
    ## 166  05 2018
    ## 167  05 2018
    ## 168  05 2018
    ## 169  05 2018
    ## 170  05 2018
    ## 171  05 2018
    ## 172  05 2018
    ## 173  05 2018
    ## 174  05 2018
    ## 175  05 2018
    ## 176  05 2018
    ## 177  05 2018
    ## 178  05 2018
    ## 179  05 2018
    ## 180  05 2018
    ## 181  05 2018
    ## 182  05 2018
    ## 183  05 2018
    ## 184  05 2018
    ## 185  05 2018
    ## 186  05 2018
    ## 187  05 2018
    ## 188  05 2018
    ## 189  05 2018
    ## 190  05 2018
    ## 191  05 2018
    ## 192  05 2018
    ## 193  05 2018
    ## 194  05 2018
    ## 195  05 2018
    ## 196  05 2018
    ## 197  05 2018
    ## 198  05 2018
    ## 199  05 2018
    ## 200  05 2018
    ## 201  05 2018
    ## 202  05 2018
    ## 203  05 2018
    ## 204  05 2018
    ## 205  05 2018
    ## 206  05 2018
    ## 207  05 2018
    ## 208  05 2018
    ## 209  05 2018
    ## 210  05 2018
    ## 211  05 2018
    ## 212  05 2018
    ## 213  05 2018
    ## 214  05 2018
    ## 215  05 2018
    ## 
    ## [[6]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10000989        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 2    10000990                          POLLO PINULITO|||FALTANTE     76001
    ## 3    10000991                                TAQUERIA EL CHINITO     76002
    ## 4    10000992            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 5    10000993            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 6    10000994                          POLLO PINULITO|||FALTANTE     76001
    ## 7    10000995      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 8    10000996                  POLLO PINULITO/Despacho a cliente     76001
    ## 9    10000997                  POLLO PINULITO/Despacho a cliente     76002
    ## 10   10000998                                TAQUERIA EL CHINITO     76001
    ## 11   10000999                     EL PINCHE OBELISCO |||Faltante     76001
    ## 12   10001000                EL GALLO NEGRO / Despacho a cliente     76001
    ## 13   10001001                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 14   10001002           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 15   10001003            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 16   10001004                              HOSPITAL LAS AMERICAS     76001
    ## 17   10001005           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 18   10001006                            UBIQUO LABS |||FALTANTE     76002
    ## 19   10001007                                     BAR LA OFICINA     76001
    ## 20   10001008                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 21   10001009           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 22   10001010            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 23   10001011           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 24   10001012                                     BAR LA OFICINA     76001
    ## 25   10001013                                TAQUERIA EL CHINITO     76001
    ## 26   10001014            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 27   10001015                              HOSPITAL LAS AMERICAS     76002
    ## 28   10001016                            UBIQUO LABS |||FALTANTE     76001
    ## 29   10001017        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 30   10001018                     EL PINCHE OBELISCO |||Faltante     76001
    ## 31   10001019            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 32   10001020           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 33   10001021                          POLLO PINULITO|||FALTANTE     76002
    ## 34   10001022                EL GALLO NEGRO / Despacho a cliente     76001
    ## 35   10001023            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 36   10001024           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 37   10001025                          POLLO PINULITO|||FALTANTE     76002
    ## 38   10001026                                        UBIQUO LABS     76001
    ## 39   10001027            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 40   10001028                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 41   10001029                     EL PINCHE OBELISCO |||Faltante     76001
    ## 42   10001030           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 43   10001031        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 44   10001032                  POLLO PINULITO/Despacho a cliente     76002
    ## 45   10001033                          POLLO PINULITO|||FALTANTE     76001
    ## 46   10001034           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 47   10001035                            UBIQUO LABS |||FALTANTE     76002
    ## 48   10001036                                TAQUERIA EL CHINITO     76001
    ## 49   10001037        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 50   10001038        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 51   10001039            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 52   10001040                                        UBIQUO LABS     76001
    ## 53   10001041                EL GALLO NEGRO / Despacho a cliente     76002
    ## 54   10001042                                     BAR LA OFICINA     76001
    ## 55   10001043            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 56   10001044                          POLLO PINULITO|||FALTANTE     76001
    ## 57   10001045                EL GALLO NEGRO / Despacho a cliente     76002
    ## 58   10001046                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 59   10001047                          POLLO PINULITO|||FALTANTE     76001
    ## 60   10001048                EL GALLO NEGRO / Despacho a cliente     76002
    ## 61   10001049            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 62   10001050                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 63   10001051                          POLLO PINULITO|||FALTANTE     76001
    ## 64   10001052           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 65   10001053                              HOSPITAL LAS AMERICAS     76002
    ## 66   10001054                EL GALLO NEGRO / Despacho a cliente     76002
    ## 67   10001055                            UBIQUO LABS |||FALTANTE     76002
    ## 68   10001056                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 69   10001057           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 70   10001058                          POLLO PINULITO|||FALTANTE     76001
    ## 71   10001059        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 72   10001060           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 73   10001061                     EL PINCHE OBELISCO |||Faltante     76002
    ## 74   10001062                            UBIQUO LABS |||FALTANTE     76001
    ## 75   10001063                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 76   10001064      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 77   10001065                            UBIQUO LABS |||FALTANTE     76001
    ## 78   10001066 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 79   10001067                                     BAR LA OFICINA     76002
    ## 80   10001068           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 81   10001069            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 82   10001070                                        UBIQUO LABS     76001
    ## 83   10001071        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 84   10001072                  POLLO PINULITO/Despacho a cliente     76002
    ## 85   10001073            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 86   10001074                            UBIQUO LABS |||FALTANTE     76002
    ## 87   10001075           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 88   10001076                              HOSPITAL LAS AMERICAS     76002
    ## 89   10001077                  POLLO PINULITO/Despacho a cliente     76002
    ## 90   10001078                          POLLO PINULITO|||FALTANTE     76002
    ## 91   10001079                                     BAR LA OFICINA     76002
    ## 92   10001080            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 93   10001081 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 94   10001082                                TAQUERIA EL CHINITO     76002
    ## 95   10001083                  POLLO PINULITO/Despacho a cliente     76001
    ## 96   10001084                                     BAR LA OFICINA     76002
    ## 97   10001085      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 98   10001086                                TAQUERIA EL CHINITO     76001
    ## 99   10001087                                        UBIQUO LABS     76002
    ## 100  10001088                                        UBIQUO LABS     76002
    ## 101  10001089                                     BAR LA OFICINA     76001
    ## 102  10001090                                     BAR LA OFICINA     76001
    ## 103  10001091            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 104  10001092                                        UBIQUO LABS     76002
    ## 105  10001093                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 106  10001094                              HOSPITAL LAS AMERICAS     76001
    ## 107  10001095                                     BAR LA OFICINA     76001
    ## 108  10001096 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 109  10001097        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 110  10001098      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 111  10001099                            UBIQUO LABS |||FALTANTE     76002
    ## 112  10001100 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 113  10001101           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 114  10001102      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 115  10001103                     EL PINCHE OBELISCO |||Faltante     76002
    ## 116  10001104           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 117  10001105           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 118  10001106                                TAQUERIA EL CHINITO     76001
    ## 119  10001107                                        UBIQUO LABS     76001
    ## 120  10001108                EL GALLO NEGRO / Despacho a cliente     76001
    ## 121  10001109            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 122  10001110                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 123  10001111                          POLLO PINULITO|||FALTANTE     76001
    ## 124  10001112                          POLLO PINULITO|||FALTANTE     76002
    ## 125  10001113                                TAQUERIA EL CHINITO     76002
    ## 126  10001114                     EL PINCHE OBELISCO |||Faltante     76002
    ## 127  10001115           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 128  10001116                          POLLO PINULITO|||FALTANTE     76002
    ## 129  10001117                              HOSPITAL LAS AMERICAS     76001
    ## 130  10001118                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 131  10001119           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 132  10001120                          POLLO PINULITO|||FALTANTE     76002
    ## 133  10001121           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 134  10001122                  POLLO PINULITO/Despacho a cliente     76002
    ## 135  10001123                  POLLO PINULITO/Despacho a cliente     76001
    ## 136  10001124                  POLLO PINULITO/Despacho a cliente     76002
    ## 137  10001125                                TAQUERIA EL CHINITO     76001
    ## 138  10001126                                        UBIQUO LABS     76002
    ## 139  10001127                EL GALLO NEGRO / Despacho a cliente     76001
    ## 140  10001128        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 141  10001129                                TAQUERIA EL CHINITO     76001
    ## 142  10001130                                        UBIQUO LABS     76002
    ## 143  10001131                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 144  10001132                                TAQUERIA EL CHINITO     76001
    ## 145  10001133                          POLLO PINULITO|||FALTANTE     76001
    ## 146  10001134                                TAQUERIA EL CHINITO     76002
    ## 147  10001135        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 148  10001136        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 149  10001137      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 150  10001138            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 151  10001139        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 152  10001140                              HOSPITAL LAS AMERICAS     76001
    ## 153  10001141                                     BAR LA OFICINA     76002
    ## 154  10001142                                TAQUERIA EL CHINITO     76001
    ## 155  10001143                                        UBIQUO LABS     76001
    ## 156  10001144                EL GALLO NEGRO / Despacho a cliente     76001
    ## 157  10001145        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 158  10001146            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 159  10001147 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 160  10001148                                TAQUERIA EL CHINITO     76002
    ## 161  10001149 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 162  10001150           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 163  10001151                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 164  10001152      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 165  10001153                  POLLO PINULITO/Despacho a cliente     76001
    ## 166  10001154                            UBIQUO LABS |||FALTANTE     76001
    ## 167  10001155                     EL PINCHE OBELISCO |||Faltante     76001
    ## 168  10001156                     EL PINCHE OBELISCO |||Faltante     76001
    ## 169  10001157                     EL PINCHE OBELISCO |||Faltante     76001
    ## 170  10001158           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 171  10001159                     EL PINCHE OBELISCO |||Faltante     76002
    ## 172  10001160                EL GALLO NEGRO / Despacho a cliente     76001
    ## 173  10001161                EL GALLO NEGRO / Despacho a cliente     76002
    ## 174  10001162                              HOSPITAL LAS AMERICAS     76001
    ## 175  10001163      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 176  10001164                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 177  10001165            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 178  10001166            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 179  10001167      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 180  10001168            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 181  10001169                                     BAR LA OFICINA     76001
    ## 182  10001170                          POLLO PINULITO|||FALTANTE     76001
    ## 183  10001171                                        UBIQUO LABS     76001
    ## 184  10001172                                        UBIQUO LABS     76002
    ## 185  10001173                                        UBIQUO LABS     76001
    ## 186  10001174                              HOSPITAL LAS AMERICAS     76002
    ## 187  10001175                     EL PINCHE OBELISCO |||Faltante     76002
    ## 188  10001176                                     BAR LA OFICINA     76001
    ## 189  10001177                            UBIQUO LABS |||FALTANTE     76002
    ## 190  10001178                     EL PINCHE OBELISCO |||Faltante     76002
    ## 191  10001179 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 192  10001180                            UBIQUO LABS |||FALTANTE     76001
    ## 193  10001181           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 194  10001182                              HOSPITAL LAS AMERICAS     76001
    ## 195  10001183            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 196  10001184                  POLLO PINULITO/Despacho a cliente     76001
    ## 197  10001185 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1325          Pedro Alvarez Parejo 331.25      30  Camion Grande
    ## 2        497                  Hector Giron 124.25      60          Panel
    ## 3       1177       Fernando Mariano Berrio 294.25      60  Camion Grande
    ## 4       1872      Ismael Rodero Monteagudo 468.00      90  Camion Grande
    ## 5       1663                  Hector Giron 415.75      90  Camion Grande
    ## 6       1657          Pedro Alvarez Parejo 414.25      90  Camion Grande
    ## 7        457          Angel Valdez Alegria 114.25      60          Panel
    ## 8       1574              Felipe Villatoro 393.50      30  Camion Grande
    ## 9        904        Hector Aragones Frutos 226.00      30 Camion Pequeño
    ## 10      1939        Hector Aragones Frutos 484.75      90  Camion Grande
    ## 11      1852             Luis Jaime Urbano 463.00      60  Camion Grande
    ## 12      1909        Hector Aragones Frutos 477.25      90  Camion Grande
    ## 13      1411              Felipe Villatoro 352.75      90  Camion Grande
    ## 14       398       Fernando Mariano Berrio  99.50      60          Panel
    ## 15       251        Hector Aragones Frutos  62.75      60          Panel
    ## 16       235        Hector Aragones Frutos  58.75      90          Panel
    ## 17      1026              Felipe Villatoro 256.50      60  Camion Grande
    ## 18      1221                  Hector Giron 305.25      90  Camion Grande
    ## 19       313          Angel Valdez Alegria  78.25      90          Panel
    ## 20      1474                  Hector Giron 368.50      30  Camion Grande
    ## 21      1194                  Hector Giron 298.50      60  Camion Grande
    ## 22      1147        Hector Aragones Frutos 286.75      60  Camion Grande
    ## 23       439          Pedro Alvarez Parejo 109.75      60          Panel
    ## 24      1748       Fernando Mariano Berrio 437.00      60  Camion Grande
    ## 25       577      Ismael Rodero Monteagudo 144.25      60 Camion Pequeño
    ## 26      1550        Hector Aragones Frutos 387.50      60  Camion Grande
    ## 27       319 Juan Francisco Portillo Gomez  79.75      90          Panel
    ## 28       960                  Hector Giron 240.00      90 Camion Pequeño
    ## 29       264          Pedro Alvarez Parejo  66.00      90          Panel
    ## 30       859              Felipe Villatoro 214.75      30 Camion Pequeño
    ## 31      1210                  Hector Giron 302.50      60  Camion Grande
    ## 32      1592          Angel Valdez Alegria 398.00      30  Camion Grande
    ## 33      1186              Felipe Villatoro 296.50      30  Camion Grande
    ## 34      1763          Angel Valdez Alegria 440.75      60  Camion Grande
    ## 35       217              Felipe Villatoro  54.25      60          Panel
    ## 36      1783      Ismael Rodero Monteagudo 445.75      90  Camion Grande
    ## 37       805      Ismael Rodero Monteagudo 201.25      90 Camion Pequeño
    ## 38      1241          Angel Valdez Alegria 310.25      30  Camion Grande
    ## 39      1760                  Hector Giron 440.00      30  Camion Grande
    ## 40      1915 Juan Francisco Portillo Gomez 478.75      60  Camion Grande
    ## 41      1798             Luis Jaime Urbano 449.50      30  Camion Grande
    ## 42      1327       Fernando Mariano Berrio 331.75      30  Camion Grande
    ## 43      1167       Fernando Mariano Berrio 291.75      30  Camion Grande
    ## 44      1256      Ismael Rodero Monteagudo 314.00      60  Camion Grande
    ## 45      1290 Juan Francisco Portillo Gomez 322.50      60  Camion Grande
    ## 46       511       Fernando Mariano Berrio 127.75      90 Camion Pequeño
    ## 47       287        Hector Aragones Frutos  71.75      90          Panel
    ## 48      1318             Luis Jaime Urbano 329.50      60  Camion Grande
    ## 49       906          Pedro Alvarez Parejo 226.50      60 Camion Pequeño
    ## 50      1921          Angel Valdez Alegria 480.25      90  Camion Grande
    ## 51      1279          Pedro Alvarez Parejo 319.75      30  Camion Grande
    ## 52       445      Ismael Rodero Monteagudo 111.25      60          Panel
    ## 53      1616       Fernando Mariano Berrio 404.00      30  Camion Grande
    ## 54       868                  Hector Giron 217.00      30 Camion Pequeño
    ## 55       789          Pedro Alvarez Parejo 197.25      30 Camion Pequeño
    ## 56       547             Luis Jaime Urbano 136.75      90 Camion Pequeño
    ## 57       700              Felipe Villatoro 175.00      90 Camion Pequeño
    ## 58      1377      Ismael Rodero Monteagudo 344.25      30  Camion Grande
    ## 59      1326          Angel Valdez Alegria 331.50      60  Camion Grande
    ## 60       322 Juan Francisco Portillo Gomez  80.50      60          Panel
    ## 61       223             Luis Jaime Urbano  55.75      60          Panel
    ## 62      1767             Luis Jaime Urbano 441.75      90  Camion Grande
    ## 63      1048                  Hector Giron 262.00      90  Camion Grande
    ## 64      1114          Angel Valdez Alegria 278.50      60  Camion Grande
    ## 65       740              Felipe Villatoro 185.00      90 Camion Pequeño
    ## 66       776          Angel Valdez Alegria 194.00      60 Camion Pequeño
    ## 67       609              Felipe Villatoro 152.25      60 Camion Pequeño
    ## 68      1660             Luis Jaime Urbano 415.00      30  Camion Grande
    ## 69       272             Luis Jaime Urbano  68.00      60          Panel
    ## 70       526       Fernando Mariano Berrio 131.50      90 Camion Pequeño
    ## 71       598          Angel Valdez Alegria 149.50      90 Camion Pequeño
    ## 72       747        Hector Aragones Frutos 186.75      90 Camion Pequeño
    ## 73      1351              Felipe Villatoro 337.75      90  Camion Grande
    ## 74      1515          Angel Valdez Alegria 378.75      60  Camion Grande
    ## 75      1499          Pedro Alvarez Parejo 374.75      30  Camion Grande
    ## 76      1757          Angel Valdez Alegria 439.25      90  Camion Grande
    ## 77      1613      Ismael Rodero Monteagudo 403.25      30  Camion Grande
    ## 78      1928          Pedro Alvarez Parejo 482.00      30  Camion Grande
    ## 79      1124          Angel Valdez Alegria 281.00      30  Camion Grande
    ## 80      1052             Luis Jaime Urbano 263.00      30  Camion Grande
    ## 81      1035             Luis Jaime Urbano 258.75      90  Camion Grande
    ## 82      1275             Luis Jaime Urbano 318.75      90  Camion Grande
    ## 83       323      Ismael Rodero Monteagudo  80.75      30          Panel
    ## 84      1496             Luis Jaime Urbano 374.00      60  Camion Grande
    ## 85       771        Hector Aragones Frutos 192.75      30 Camion Pequeño
    ## 86      1625      Ismael Rodero Monteagudo 406.25      90  Camion Grande
    ## 87      1252             Luis Jaime Urbano 313.00      60  Camion Grande
    ## 88      1199       Fernando Mariano Berrio 299.75      60  Camion Grande
    ## 89      1889                  Hector Giron 472.25      90  Camion Grande
    ## 90      1051 Juan Francisco Portillo Gomez 262.75      90  Camion Grande
    ## 91       595                  Hector Giron 148.75      30 Camion Pequeño
    ## 92       965                  Hector Giron 241.25      30 Camion Pequeño
    ## 93      1615          Angel Valdez Alegria 403.75      60  Camion Grande
    ## 94       296        Hector Aragones Frutos  74.00      30          Panel
    ## 95      1784       Fernando Mariano Berrio 446.00      90  Camion Grande
    ## 96       386              Felipe Villatoro  96.50      60          Panel
    ## 97      1176             Luis Jaime Urbano 294.00      90  Camion Grande
    ## 98       259      Ismael Rodero Monteagudo  64.75      90          Panel
    ## 99       443 Juan Francisco Portillo Gomez 110.75      90          Panel
    ## 100      917       Fernando Mariano Berrio 229.25      90 Camion Pequeño
    ## 101      917 Juan Francisco Portillo Gomez 229.25      90 Camion Pequeño
    ## 102      406          Pedro Alvarez Parejo 101.50      90          Panel
    ## 103     1674       Fernando Mariano Berrio 418.50      60  Camion Grande
    ## 104      546              Felipe Villatoro 136.50      30 Camion Pequeño
    ## 105     1263                  Hector Giron 315.75      60  Camion Grande
    ## 106      509 Juan Francisco Portillo Gomez 127.25      90 Camion Pequeño
    ## 107     1840          Pedro Alvarez Parejo 460.00      30  Camion Grande
    ## 108     1472             Luis Jaime Urbano 368.00      30  Camion Grande
    ## 109      242          Pedro Alvarez Parejo  60.50      30          Panel
    ## 110      880      Ismael Rodero Monteagudo 220.00      90 Camion Pequeño
    ## 111     1028        Hector Aragones Frutos 257.00      30  Camion Grande
    ## 112     1830          Pedro Alvarez Parejo 457.50      30  Camion Grande
    ## 113      597                  Hector Giron 149.25      60 Camion Pequeño
    ## 114     1755        Hector Aragones Frutos 438.75      30  Camion Grande
    ## 115      608             Luis Jaime Urbano 152.00      90 Camion Pequeño
    ## 116      883       Fernando Mariano Berrio 220.75      30 Camion Pequeño
    ## 117      677        Hector Aragones Frutos 169.25      60 Camion Pequeño
    ## 118     1554       Fernando Mariano Berrio 388.50      30  Camion Grande
    ## 119     1004          Pedro Alvarez Parejo 251.00      60  Camion Grande
    ## 120      540                  Hector Giron 135.00      60 Camion Pequeño
    ## 121     1936                  Hector Giron 484.00      30  Camion Grande
    ## 122     1227              Felipe Villatoro 306.75      30  Camion Grande
    ## 123     1266                  Hector Giron 316.50      60  Camion Grande
    ## 124     1291              Felipe Villatoro 322.75      60  Camion Grande
    ## 125     1470        Hector Aragones Frutos 367.50      60  Camion Grande
    ## 126     1029             Luis Jaime Urbano 257.25      30  Camion Grande
    ## 127      614             Luis Jaime Urbano 153.50      30 Camion Pequeño
    ## 128      809          Pedro Alvarez Parejo 202.25      60 Camion Pequeño
    ## 129      986                  Hector Giron 246.50      90 Camion Pequeño
    ## 130     1573              Felipe Villatoro 393.25      60  Camion Grande
    ## 131      227        Hector Aragones Frutos  56.75      60          Panel
    ## 132      723                  Hector Giron 180.75      60 Camion Pequeño
    ## 133      351        Hector Aragones Frutos  87.75      60          Panel
    ## 134     1865                  Hector Giron 466.25      60  Camion Grande
    ## 135     1480             Luis Jaime Urbano 370.00      60  Camion Grande
    ## 136     1206              Felipe Villatoro 301.50      90  Camion Grande
    ## 137      576      Ismael Rodero Monteagudo 144.00      90 Camion Pequeño
    ## 138     1273      Ismael Rodero Monteagudo 318.25      30  Camion Grande
    ## 139     1598      Ismael Rodero Monteagudo 399.50      30  Camion Grande
    ## 140      318      Ismael Rodero Monteagudo  79.50      60          Panel
    ## 141      381             Luis Jaime Urbano  95.25      30          Panel
    ## 142     1342 Juan Francisco Portillo Gomez 335.50      90  Camion Grande
    ## 143     1985          Pedro Alvarez Parejo 496.25      90  Camion Grande
    ## 144      273             Luis Jaime Urbano  68.25      60          Panel
    ## 145     1008      Ismael Rodero Monteagudo 252.00      60  Camion Grande
    ## 146      633      Ismael Rodero Monteagudo 158.25      30 Camion Pequeño
    ## 147     1694 Juan Francisco Portillo Gomez 423.50      30  Camion Grande
    ## 148      359              Felipe Villatoro  89.75      30          Panel
    ## 149      282          Angel Valdez Alegria  70.50      60          Panel
    ## 150      266       Fernando Mariano Berrio  66.50      30          Panel
    ## 151     1095          Pedro Alvarez Parejo 273.75      90  Camion Grande
    ## 152     1468      Ismael Rodero Monteagudo 367.00      30  Camion Grande
    ## 153      370       Fernando Mariano Berrio  92.50      30          Panel
    ## 154     1561      Ismael Rodero Monteagudo 390.25      30  Camion Grande
    ## 155      918      Ismael Rodero Monteagudo 229.50      30 Camion Pequeño
    ## 156     1771             Luis Jaime Urbano 442.75      30  Camion Grande
    ## 157     1872        Hector Aragones Frutos 468.00      90  Camion Grande
    ## 158      860                  Hector Giron 215.00      60 Camion Pequeño
    ## 159     1270          Angel Valdez Alegria 317.50      60  Camion Grande
    ## 160     1260        Hector Aragones Frutos 315.00      90  Camion Grande
    ## 161     1762             Luis Jaime Urbano 440.50      90  Camion Grande
    ## 162     1680        Hector Aragones Frutos 420.00      30  Camion Grande
    ## 163      973        Hector Aragones Frutos 243.25      90 Camion Pequeño
    ## 164     1060       Fernando Mariano Berrio 265.00      60  Camion Grande
    ## 165      831             Luis Jaime Urbano 207.75      30 Camion Pequeño
    ## 166      864                  Hector Giron 216.00      90 Camion Pequeño
    ## 167     1564              Felipe Villatoro 391.00      30  Camion Grande
    ## 168      210             Luis Jaime Urbano  52.50      60          Panel
    ## 169      474          Angel Valdez Alegria 118.50      90          Panel
    ## 170     1484          Pedro Alvarez Parejo 371.00      30  Camion Grande
    ## 171      668             Luis Jaime Urbano 167.00      60 Camion Pequeño
    ## 172      949                  Hector Giron 237.25      30 Camion Pequeño
    ## 173     1057        Hector Aragones Frutos 264.25      30  Camion Grande
    ## 174      558 Juan Francisco Portillo Gomez 139.50      60 Camion Pequeño
    ## 175      237                  Hector Giron  59.25      90          Panel
    ## 176      549       Fernando Mariano Berrio 137.25      60 Camion Pequeño
    ## 177      530             Luis Jaime Urbano 132.50      60 Camion Pequeño
    ## 178      453              Felipe Villatoro 113.25      90          Panel
    ## 179      616       Fernando Mariano Berrio 154.00      60 Camion Pequeño
    ## 180     1973        Hector Aragones Frutos 493.25      30  Camion Grande
    ## 181      862          Angel Valdez Alegria 215.50      60 Camion Pequeño
    ## 182     1641          Angel Valdez Alegria 410.25      90  Camion Grande
    ## 183     1795              Felipe Villatoro 448.75      90  Camion Grande
    ## 184     1951             Luis Jaime Urbano 487.75      60  Camion Grande
    ## 185      358      Ismael Rodero Monteagudo  89.50      60          Panel
    ## 186      426          Pedro Alvarez Parejo 106.50      30          Panel
    ## 187     1330 Juan Francisco Portillo Gomez 332.50      90  Camion Grande
    ## 188     1595      Ismael Rodero Monteagudo 398.75      90  Camion Grande
    ## 189      294          Angel Valdez Alegria  73.50      90          Panel
    ## 190      668 Juan Francisco Portillo Gomez 167.00      30 Camion Pequeño
    ## 191      256 Juan Francisco Portillo Gomez  64.00      30          Panel
    ## 192     1959              Felipe Villatoro 489.75      30  Camion Grande
    ## 193     1970       Fernando Mariano Berrio 492.50      30  Camion Grande
    ## 194     1367        Hector Aragones Frutos 341.75      90  Camion Grande
    ## 195     1391          Angel Valdez Alegria 347.75      60  Camion Grande
    ## 196      344          Pedro Alvarez Parejo  86.00      60          Panel
    ## 197      633              Felipe Villatoro 158.25      30 Camion Pequeño
    ##     mes anio
    ## 1    06 2018
    ## 2    06 2018
    ## 3    06 2018
    ## 4    06 2018
    ## 5    06 2018
    ## 6    06 2018
    ## 7    06 2018
    ## 8    06 2018
    ## 9    06 2018
    ## 10   06 2018
    ## 11   06 2018
    ## 12   06 2018
    ## 13   06 2018
    ## 14   06 2018
    ## 15   06 2018
    ## 16   06 2018
    ## 17   06 2018
    ## 18   06 2018
    ## 19   06 2018
    ## 20   06 2018
    ## 21   06 2018
    ## 22   06 2018
    ## 23   06 2018
    ## 24   06 2018
    ## 25   06 2018
    ## 26   06 2018
    ## 27   06 2018
    ## 28   06 2018
    ## 29   06 2018
    ## 30   06 2018
    ## 31   06 2018
    ## 32   06 2018
    ## 33   06 2018
    ## 34   06 2018
    ## 35   06 2018
    ## 36   06 2018
    ## 37   06 2018
    ## 38   06 2018
    ## 39   06 2018
    ## 40   06 2018
    ## 41   06 2018
    ## 42   06 2018
    ## 43   06 2018
    ## 44   06 2018
    ## 45   06 2018
    ## 46   06 2018
    ## 47   06 2018
    ## 48   06 2018
    ## 49   06 2018
    ## 50   06 2018
    ## 51   06 2018
    ## 52   06 2018
    ## 53   06 2018
    ## 54   06 2018
    ## 55   06 2018
    ## 56   06 2018
    ## 57   06 2018
    ## 58   06 2018
    ## 59   06 2018
    ## 60   06 2018
    ## 61   06 2018
    ## 62   06 2018
    ## 63   06 2018
    ## 64   06 2018
    ## 65   06 2018
    ## 66   06 2018
    ## 67   06 2018
    ## 68   06 2018
    ## 69   06 2018
    ## 70   06 2018
    ## 71   06 2018
    ## 72   06 2018
    ## 73   06 2018
    ## 74   06 2018
    ## 75   06 2018
    ## 76   06 2018
    ## 77   06 2018
    ## 78   06 2018
    ## 79   06 2018
    ## 80   06 2018
    ## 81   06 2018
    ## 82   06 2018
    ## 83   06 2018
    ## 84   06 2018
    ## 85   06 2018
    ## 86   06 2018
    ## 87   06 2018
    ## 88   06 2018
    ## 89   06 2018
    ## 90   06 2018
    ## 91   06 2018
    ## 92   06 2018
    ## 93   06 2018
    ## 94   06 2018
    ## 95   06 2018
    ## 96   06 2018
    ## 97   06 2018
    ## 98   06 2018
    ## 99   06 2018
    ## 100  06 2018
    ## 101  06 2018
    ## 102  06 2018
    ## 103  06 2018
    ## 104  06 2018
    ## 105  06 2018
    ## 106  06 2018
    ## 107  06 2018
    ## 108  06 2018
    ## 109  06 2018
    ## 110  06 2018
    ## 111  06 2018
    ## 112  06 2018
    ## 113  06 2018
    ## 114  06 2018
    ## 115  06 2018
    ## 116  06 2018
    ## 117  06 2018
    ## 118  06 2018
    ## 119  06 2018
    ## 120  06 2018
    ## 121  06 2018
    ## 122  06 2018
    ## 123  06 2018
    ## 124  06 2018
    ## 125  06 2018
    ## 126  06 2018
    ## 127  06 2018
    ## 128  06 2018
    ## 129  06 2018
    ## 130  06 2018
    ## 131  06 2018
    ## 132  06 2018
    ## 133  06 2018
    ## 134  06 2018
    ## 135  06 2018
    ## 136  06 2018
    ## 137  06 2018
    ## 138  06 2018
    ## 139  06 2018
    ## 140  06 2018
    ## 141  06 2018
    ## 142  06 2018
    ## 143  06 2018
    ## 144  06 2018
    ## 145  06 2018
    ## 146  06 2018
    ## 147  06 2018
    ## 148  06 2018
    ## 149  06 2018
    ## 150  06 2018
    ## 151  06 2018
    ## 152  06 2018
    ## 153  06 2018
    ## 154  06 2018
    ## 155  06 2018
    ## 156  06 2018
    ## 157  06 2018
    ## 158  06 2018
    ## 159  06 2018
    ## 160  06 2018
    ## 161  06 2018
    ## 162  06 2018
    ## 163  06 2018
    ## 164  06 2018
    ## 165  06 2018
    ## 166  06 2018
    ## 167  06 2018
    ## 168  06 2018
    ## 169  06 2018
    ## 170  06 2018
    ## 171  06 2018
    ## 172  06 2018
    ## 173  06 2018
    ## 174  06 2018
    ## 175  06 2018
    ## 176  06 2018
    ## 177  06 2018
    ## 178  06 2018
    ## 179  06 2018
    ## 180  06 2018
    ## 181  06 2018
    ## 182  06 2018
    ## 183  06 2018
    ## 184  06 2018
    ## 185  06 2018
    ## 186  06 2018
    ## 187  06 2018
    ## 188  06 2018
    ## 189  06 2018
    ## 190  06 2018
    ## 191  06 2018
    ## 192  06 2018
    ## 193  06 2018
    ## 194  06 2018
    ## 195  06 2018
    ## 196  06 2018
    ## 197  06 2018
    ## 
    ## [[7]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10001186                EL GALLO NEGRO / Despacho a cliente     76001
    ## 2    10001187           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 3    10001188        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 4    10001189           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 5    10001190                                     BAR LA OFICINA     76002
    ## 6    10001191        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 7    10001192                                        UBIQUO LABS     76002
    ## 8    10001193      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 9    10001194            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 10   10001195 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 11   10001196                                TAQUERIA EL CHINITO     76001
    ## 12   10001197           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 13   10001198           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 14   10001199                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 15   10001200                              HOSPITAL LAS AMERICAS     76001
    ## 16   10001201                            UBIQUO LABS |||FALTANTE     76001
    ## 17   10001202 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 18   10001203                                TAQUERIA EL CHINITO     76002
    ## 19   10001204            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 20   10001205                            UBIQUO LABS |||FALTANTE     76001
    ## 21   10001206                     EL PINCHE OBELISCO |||Faltante     76002
    ## 22   10001207            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 23   10001208                  POLLO PINULITO/Despacho a cliente     76001
    ## 24   10001209                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 25   10001210                EL GALLO NEGRO / Despacho a cliente     76002
    ## 26   10001211            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 27   10001212                              HOSPITAL LAS AMERICAS     76002
    ## 28   10001213                                TAQUERIA EL CHINITO     76001
    ## 29   10001214                          POLLO PINULITO|||FALTANTE     76001
    ## 30   10001215 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 31   10001216            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 32   10001217           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 33   10001218                  POLLO PINULITO/Despacho a cliente     76002
    ## 34   10001219                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 35   10001220                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 36   10001221                          POLLO PINULITO|||FALTANTE     76001
    ## 37   10001222                                     BAR LA OFICINA     76002
    ## 38   10001223                            UBIQUO LABS |||FALTANTE     76002
    ## 39   10001224                              HOSPITAL LAS AMERICAS     76001
    ## 40   10001225           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 41   10001226        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 42   10001227                     EL PINCHE OBELISCO |||Faltante     76002
    ## 43   10001228      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 44   10001229           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 45   10001230            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 46   10001231                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 47   10001232      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 48   10001233        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 49   10001234           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 50   10001235                  POLLO PINULITO/Despacho a cliente     76001
    ## 51   10001236                            UBIQUO LABS |||FALTANTE     76002
    ## 52   10001237                                TAQUERIA EL CHINITO     76001
    ## 53   10001238                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 54   10001239                  POLLO PINULITO/Despacho a cliente     76002
    ## 55   10001240                EL GALLO NEGRO / Despacho a cliente     76002
    ## 56   10001241                                        UBIQUO LABS     76001
    ## 57   10001242                          POLLO PINULITO|||FALTANTE     76001
    ## 58   10001243            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 59   10001244 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 60   10001245           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 61   10001246                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 62   10001247                          POLLO PINULITO|||FALTANTE     76002
    ## 63   10001248                EL GALLO NEGRO / Despacho a cliente     76002
    ## 64   10001249            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 65   10001250                            UBIQUO LABS |||FALTANTE     76001
    ## 66   10001251                     EL PINCHE OBELISCO |||Faltante     76002
    ## 67   10001252            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 68   10001253                                     BAR LA OFICINA     76001
    ## 69   10001254                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 70   10001255 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 71   10001256                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 72   10001257           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 73   10001258                              HOSPITAL LAS AMERICAS     76001
    ## 74   10001259                          POLLO PINULITO|||FALTANTE     76001
    ## 75   10001260           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 76   10001261                                TAQUERIA EL CHINITO     76002
    ## 77   10001262                                     BAR LA OFICINA     76001
    ## 78   10001263                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 79   10001264                  POLLO PINULITO/Despacho a cliente     76002
    ## 80   10001265        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 81   10001266           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 82   10001267                                     BAR LA OFICINA     76002
    ## 83   10001268                            UBIQUO LABS |||FALTANTE     76002
    ## 84   10001269                EL GALLO NEGRO / Despacho a cliente     76001
    ## 85   10001270            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 86   10001271                            UBIQUO LABS |||FALTANTE     76002
    ## 87   10001272                            UBIQUO LABS |||FALTANTE     76002
    ## 88   10001273        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 89   10001274                     EL PINCHE OBELISCO |||Faltante     76002
    ## 90   10001275        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 91   10001276                            UBIQUO LABS |||FALTANTE     76001
    ## 92   10001277                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 93   10001278                     EL PINCHE OBELISCO |||Faltante     76001
    ## 94   10001279                  POLLO PINULITO/Despacho a cliente     76001
    ## 95   10001280                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 96   10001281                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 97   10001282                                        UBIQUO LABS     76002
    ## 98   10001283                                TAQUERIA EL CHINITO     76002
    ## 99   10001284            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 100  10001285 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 101  10001286                EL GALLO NEGRO / Despacho a cliente     76001
    ## 102  10001287        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 103  10001288 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 104  10001289                              HOSPITAL LAS AMERICAS     76001
    ## 105  10001290            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 106  10001291                                TAQUERIA EL CHINITO     76001
    ## 107  10001292                              HOSPITAL LAS AMERICAS     76002
    ## 108  10001293                            UBIQUO LABS |||FALTANTE     76001
    ## 109  10001294                  POLLO PINULITO/Despacho a cliente     76002
    ## 110  10001295      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 111  10001296                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 112  10001297            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 113  10001298            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 114  10001299 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 115  10001300                          POLLO PINULITO|||FALTANTE     76002
    ## 116  10001301                          POLLO PINULITO|||FALTANTE     76002
    ## 117  10001302                                TAQUERIA EL CHINITO     76002
    ## 118  10001303           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 119  10001304                     EL PINCHE OBELISCO |||Faltante     76001
    ## 120  10001305                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 121  10001306                  POLLO PINULITO/Despacho a cliente     76001
    ## 122  10001307                                        UBIQUO LABS     76001
    ## 123  10001308                  POLLO PINULITO/Despacho a cliente     76002
    ## 124  10001309           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 125  10001310      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 126  10001311           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 127  10001312            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 128  10001313                EL GALLO NEGRO / Despacho a cliente     76001
    ## 129  10001314            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 130  10001315                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 131  10001316                  POLLO PINULITO/Despacho a cliente     76002
    ## 132  10001317                              HOSPITAL LAS AMERICAS     76001
    ## 133  10001318           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 134  10001319                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 135  10001320                     EL PINCHE OBELISCO |||Faltante     76002
    ## 136  10001321            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 137  10001322                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 138  10001323        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 139  10001324                                        UBIQUO LABS     76002
    ## 140  10001325           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 141  10001326                            UBIQUO LABS |||FALTANTE     76002
    ## 142  10001327                                     BAR LA OFICINA     76001
    ## 143  10001328                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 144  10001329                  POLLO PINULITO/Despacho a cliente     76002
    ## 145  10001330                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 146  10001331 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 147  10001332                                     BAR LA OFICINA     76001
    ## 148  10001333           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 149  10001334            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 150  10001335                                        UBIQUO LABS     76001
    ## 151  10001336                EL GALLO NEGRO / Despacho a cliente     76002
    ## 152  10001337                                TAQUERIA EL CHINITO     76002
    ## 153  10001338           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 154  10001339                          POLLO PINULITO|||FALTANTE     76002
    ## 155  10001340                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 156  10001341           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 157  10001342                     EL PINCHE OBELISCO |||Faltante     76001
    ## 158  10001343                  POLLO PINULITO/Despacho a cliente     76002
    ## 159  10001344                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 160  10001345                            UBIQUO LABS |||FALTANTE     76002
    ## 161  10001346                                     BAR LA OFICINA     76001
    ## 162  10001347           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 163  10001348        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 164  10001349                EL GALLO NEGRO / Despacho a cliente     76001
    ## 165  10001350      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 166  10001351                                     BAR LA OFICINA     76001
    ## 167  10001352                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 168  10001353      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 169  10001354      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 170  10001355                  POLLO PINULITO/Despacho a cliente     76001
    ## 171  10001356                     EL PINCHE OBELISCO |||Faltante     76001
    ## 172  10001357                                     BAR LA OFICINA     76001
    ## 173  10001358                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 174  10001359                              HOSPITAL LAS AMERICAS     76002
    ## 175  10001360                     EL PINCHE OBELISCO |||Faltante     76002
    ## 176  10001361                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 177  10001362                     EL PINCHE OBELISCO |||Faltante     76002
    ## 178  10001363      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 179  10001364 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 180  10001365 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 181  10001366                     EL PINCHE OBELISCO |||Faltante     76001
    ## 182  10001367            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 183  10001368                  POLLO PINULITO/Despacho a cliente     76001
    ## 184  10001369                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 185  10001370                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 186  10001371                EL GALLO NEGRO / Despacho a cliente     76002
    ## 187  10001372           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 188  10001373 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 189  10001374            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 190  10001375            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 191  10001376                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 192  10001377                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 193  10001378                                     BAR LA OFICINA     76002
    ## 194  10001379                          POLLO PINULITO|||FALTANTE     76002
    ## 195  10001380            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 196  10001381                     EL PINCHE OBELISCO |||Faltante     76001
    ## 197  10001382        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 198  10001383                                        UBIQUO LABS     76001
    ## 199  10001384                            UBIQUO LABS |||FALTANTE     76001
    ## 200  10001385                                     BAR LA OFICINA     76001
    ## 201  10001386                                        UBIQUO LABS     76002
    ## 202  10001387            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 203  10001388 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 204  10001389                                TAQUERIA EL CHINITO     76002
    ## 205  10001390           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 206  10001391           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 207  10001392           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 208  10001393                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 209  10001394                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 210  10001395                          POLLO PINULITO|||FALTANTE     76001
    ## 211  10001396      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1085       Fernando Mariano Berrio 271.25      60  Camion Grande
    ## 2       1212          Angel Valdez Alegria 303.00      60  Camion Grande
    ## 3        899        Hector Aragones Frutos 224.75      30 Camion Pequeño
    ## 4       1562       Fernando Mariano Berrio 390.50      30  Camion Grande
    ## 5       1113          Angel Valdez Alegria 278.25      30  Camion Grande
    ## 6        446          Pedro Alvarez Parejo 111.50      30          Panel
    ## 7       1517             Luis Jaime Urbano 379.25      90  Camion Grande
    ## 8        570                  Hector Giron 142.50      60 Camion Pequeño
    ## 9       1619          Pedro Alvarez Parejo 404.75      60  Camion Grande
    ## 10       213      Ismael Rodero Monteagudo  53.25      30          Panel
    ## 11       318      Ismael Rodero Monteagudo  79.50      30          Panel
    ## 12       956          Angel Valdez Alegria 239.00      30 Camion Pequeño
    ## 13       948                  Hector Giron 237.00      30 Camion Pequeño
    ## 14       447 Juan Francisco Portillo Gomez 111.75      60          Panel
    ## 15      1752              Felipe Villatoro 438.00      60  Camion Grande
    ## 16       247              Felipe Villatoro  61.75      30          Panel
    ## 17       627          Angel Valdez Alegria 156.75      90 Camion Pequeño
    ## 18      1334          Angel Valdez Alegria 333.50      90  Camion Grande
    ## 19      1297                  Hector Giron 324.25      30  Camion Grande
    ## 20       518          Angel Valdez Alegria 129.50      30 Camion Pequeño
    ## 21      1162 Juan Francisco Portillo Gomez 290.50      90  Camion Grande
    ## 22      1088          Pedro Alvarez Parejo 272.00      30  Camion Grande
    ## 23       994       Fernando Mariano Berrio 248.50      90 Camion Pequeño
    ## 24      1368              Felipe Villatoro 342.00      90  Camion Grande
    ## 25      1839              Felipe Villatoro 459.75      30  Camion Grande
    ## 26      1574              Felipe Villatoro 393.50      30  Camion Grande
    ## 27       259          Angel Valdez Alegria  64.75      60          Panel
    ## 28       267      Ismael Rodero Monteagudo  66.75      30          Panel
    ## 29      1794        Hector Aragones Frutos 448.50      30  Camion Grande
    ## 30       855          Pedro Alvarez Parejo 213.75      60 Camion Pequeño
    ## 31      1322      Ismael Rodero Monteagudo 330.50      60  Camion Grande
    ## 32      1696                  Hector Giron 424.00      60  Camion Grande
    ## 33      1532      Ismael Rodero Monteagudo 383.00      30  Camion Grande
    ## 34      1769       Fernando Mariano Berrio 442.25      90  Camion Grande
    ## 35      1864              Felipe Villatoro 466.00      30  Camion Grande
    ## 36       225                  Hector Giron  56.25      60          Panel
    ## 37      1434             Luis Jaime Urbano 358.50      30  Camion Grande
    ## 38       836             Luis Jaime Urbano 209.00      90 Camion Pequeño
    ## 39      1703             Luis Jaime Urbano 425.75      90  Camion Grande
    ## 40      1369 Juan Francisco Portillo Gomez 342.25      30  Camion Grande
    ## 41      1577      Ismael Rodero Monteagudo 394.25      60  Camion Grande
    ## 42       778        Hector Aragones Frutos 194.50      30 Camion Pequeño
    ## 43      1451 Juan Francisco Portillo Gomez 362.75      60  Camion Grande
    ## 44       784          Pedro Alvarez Parejo 196.00      90 Camion Pequeño
    ## 45       206      Ismael Rodero Monteagudo  51.50      30          Panel
    ## 46       269       Fernando Mariano Berrio  67.25      30          Panel
    ## 47       562          Pedro Alvarez Parejo 140.50      30 Camion Pequeño
    ## 48      1251       Fernando Mariano Berrio 312.75      60  Camion Grande
    ## 49      1031 Juan Francisco Portillo Gomez 257.75      90  Camion Grande
    ## 50       663      Ismael Rodero Monteagudo 165.75      60 Camion Pequeño
    ## 51      1852 Juan Francisco Portillo Gomez 463.00      30  Camion Grande
    ## 52       847       Fernando Mariano Berrio 211.75      30 Camion Pequeño
    ## 53      1144          Pedro Alvarez Parejo 286.00      30  Camion Grande
    ## 54      1564             Luis Jaime Urbano 391.00      30  Camion Grande
    ## 55      1349              Felipe Villatoro 337.25      60  Camion Grande
    ## 56       467                  Hector Giron 116.75      60          Panel
    ## 57      1353          Angel Valdez Alegria 338.25      90  Camion Grande
    ## 58      1122 Juan Francisco Portillo Gomez 280.50      90  Camion Grande
    ## 59       357 Juan Francisco Portillo Gomez  89.25      30          Panel
    ## 60       921                  Hector Giron 230.25      90 Camion Pequeño
    ## 61       520              Felipe Villatoro 130.00      30 Camion Pequeño
    ## 62      1144      Ismael Rodero Monteagudo 286.00      30  Camion Grande
    ## 63       808       Fernando Mariano Berrio 202.00      30 Camion Pequeño
    ## 64      1627             Luis Jaime Urbano 406.75      60  Camion Grande
    ## 65       665        Hector Aragones Frutos 166.25      90 Camion Pequeño
    ## 66      1793              Felipe Villatoro 448.25      30  Camion Grande
    ## 67      1393                  Hector Giron 348.25      30  Camion Grande
    ## 68       625 Juan Francisco Portillo Gomez 156.25      90 Camion Pequeño
    ## 69      1063              Felipe Villatoro 265.75      30  Camion Grande
    ## 70      1461      Ismael Rodero Monteagudo 365.25      30  Camion Grande
    ## 71      1564          Pedro Alvarez Parejo 391.00      30  Camion Grande
    ## 72      1309       Fernando Mariano Berrio 327.25      30  Camion Grande
    ## 73      1475       Fernando Mariano Berrio 368.75      90  Camion Grande
    ## 74       581          Angel Valdez Alegria 145.25      60 Camion Pequeño
    ## 75      1787          Pedro Alvarez Parejo 446.75      90  Camion Grande
    ## 76      1363                  Hector Giron 340.75      30  Camion Grande
    ## 77      1550                  Hector Giron 387.50      90  Camion Grande
    ## 78      1408                  Hector Giron 352.00      60  Camion Grande
    ## 79       725 Juan Francisco Portillo Gomez 181.25      30 Camion Pequeño
    ## 80      1452        Hector Aragones Frutos 363.00      90  Camion Grande
    ## 81      1080             Luis Jaime Urbano 270.00      60  Camion Grande
    ## 82      1919        Hector Aragones Frutos 479.75      30  Camion Grande
    ## 83      1205        Hector Aragones Frutos 301.25      60  Camion Grande
    ## 84      1917       Fernando Mariano Berrio 479.25      90  Camion Grande
    ## 85      1852              Felipe Villatoro 463.00      90  Camion Grande
    ## 86      1690          Pedro Alvarez Parejo 422.50      30  Camion Grande
    ## 87       725        Hector Aragones Frutos 181.25      60 Camion Pequeño
    ## 88       260                  Hector Giron  65.00      90          Panel
    ## 89      1330                  Hector Giron 332.50      90  Camion Grande
    ## 90       439              Felipe Villatoro 109.75      60          Panel
    ## 91       390      Ismael Rodero Monteagudo  97.50      90          Panel
    ## 92      1605       Fernando Mariano Berrio 401.25      90  Camion Grande
    ## 93      1785              Felipe Villatoro 446.25      60  Camion Grande
    ## 94      1321              Felipe Villatoro 330.25      90  Camion Grande
    ## 95       455          Pedro Alvarez Parejo 113.75      90          Panel
    ## 96       400 Juan Francisco Portillo Gomez 100.00      60          Panel
    ## 97      1536       Fernando Mariano Berrio 384.00      60  Camion Grande
    ## 98      1506              Felipe Villatoro 376.50      60  Camion Grande
    ## 99      1444          Pedro Alvarez Parejo 361.00      60  Camion Grande
    ## 100     1336       Fernando Mariano Berrio 334.00      30  Camion Grande
    ## 101     1114 Juan Francisco Portillo Gomez 278.50      60  Camion Grande
    ## 102      417              Felipe Villatoro 104.25      90          Panel
    ## 103     1460      Ismael Rodero Monteagudo 365.00      60  Camion Grande
    ## 104     1444        Hector Aragones Frutos 361.00      30  Camion Grande
    ## 105     1985        Hector Aragones Frutos 496.25      60  Camion Grande
    ## 106      474        Hector Aragones Frutos 118.50      30          Panel
    ## 107      528              Felipe Villatoro 132.00      60 Camion Pequeño
    ## 108     1295       Fernando Mariano Berrio 323.75      30  Camion Grande
    ## 109      735          Pedro Alvarez Parejo 183.75      30 Camion Pequeño
    ## 110     1207 Juan Francisco Portillo Gomez 301.75      30  Camion Grande
    ## 111     1840      Ismael Rodero Monteagudo 460.00      60  Camion Grande
    ## 112      217        Hector Aragones Frutos  54.25      60          Panel
    ## 113     1568          Pedro Alvarez Parejo 392.00      90  Camion Grande
    ## 114      540      Ismael Rodero Monteagudo 135.00      60 Camion Pequeño
    ## 115     1292 Juan Francisco Portillo Gomez 323.00      90  Camion Grande
    ## 116     1445          Angel Valdez Alegria 361.25      60  Camion Grande
    ## 117     1083              Felipe Villatoro 270.75      30  Camion Grande
    ## 118     1290      Ismael Rodero Monteagudo 322.50      30  Camion Grande
    ## 119     1479          Angel Valdez Alegria 369.75      60  Camion Grande
    ## 120      867        Hector Aragones Frutos 216.75      30 Camion Pequeño
    ## 121      673      Ismael Rodero Monteagudo 168.25      60 Camion Pequeño
    ## 122      658             Luis Jaime Urbano 164.50      30 Camion Pequeño
    ## 123     1673       Fernando Mariano Berrio 418.25      60  Camion Grande
    ## 124     1462      Ismael Rodero Monteagudo 365.50      60  Camion Grande
    ## 125     1333      Ismael Rodero Monteagudo 333.25      30  Camion Grande
    ## 126      593          Pedro Alvarez Parejo 148.25      90 Camion Pequeño
    ## 127      223 Juan Francisco Portillo Gomez  55.75      30          Panel
    ## 128     1486 Juan Francisco Portillo Gomez 371.50      60  Camion Grande
    ## 129     1684      Ismael Rodero Monteagudo 421.00      30  Camion Grande
    ## 130     1957       Fernando Mariano Berrio 489.25      60  Camion Grande
    ## 131      221      Ismael Rodero Monteagudo  55.25      60          Panel
    ## 132      604             Luis Jaime Urbano 151.00      60 Camion Pequeño
    ## 133     1619          Angel Valdez Alegria 404.75      60  Camion Grande
    ## 134      355          Pedro Alvarez Parejo  88.75      60          Panel
    ## 135     1524          Pedro Alvarez Parejo 381.00      90  Camion Grande
    ## 136     1178        Hector Aragones Frutos 294.50      30  Camion Grande
    ## 137     1174          Pedro Alvarez Parejo 293.50      90  Camion Grande
    ## 138      645              Felipe Villatoro 161.25      90 Camion Pequeño
    ## 139     1368              Felipe Villatoro 342.00      90  Camion Grande
    ## 140      652                  Hector Giron 163.00      30 Camion Pequeño
    ## 141      866 Juan Francisco Portillo Gomez 216.50      30 Camion Pequeño
    ## 142     1337          Pedro Alvarez Parejo 334.25      90  Camion Grande
    ## 143      570              Felipe Villatoro 142.50      60 Camion Pequeño
    ## 144      484 Juan Francisco Portillo Gomez 121.00      60          Panel
    ## 145     1858          Angel Valdez Alegria 464.50      60  Camion Grande
    ## 146     1427       Fernando Mariano Berrio 356.75      90  Camion Grande
    ## 147     1920             Luis Jaime Urbano 480.00      30  Camion Grande
    ## 148     1183      Ismael Rodero Monteagudo 295.75      30  Camion Grande
    ## 149     1536          Angel Valdez Alegria 384.00      90  Camion Grande
    ## 150     1063          Angel Valdez Alegria 265.75      30  Camion Grande
    ## 151     1981             Luis Jaime Urbano 495.25      60  Camion Grande
    ## 152      298        Hector Aragones Frutos  74.50      30          Panel
    ## 153      356             Luis Jaime Urbano  89.00      90          Panel
    ## 154      915      Ismael Rodero Monteagudo 228.75      60 Camion Pequeño
    ## 155      214      Ismael Rodero Monteagudo  53.50      60          Panel
    ## 156     1811          Angel Valdez Alegria 452.75      30  Camion Grande
    ## 157     1349      Ismael Rodero Monteagudo 337.25      60  Camion Grande
    ## 158      652          Pedro Alvarez Parejo 163.00      30 Camion Pequeño
    ## 159      437             Luis Jaime Urbano 109.25      60          Panel
    ## 160      583 Juan Francisco Portillo Gomez 145.75      60 Camion Pequeño
    ## 161     1818                  Hector Giron 454.50      30  Camion Grande
    ## 162     1811             Luis Jaime Urbano 452.75      60  Camion Grande
    ## 163     1938       Fernando Mariano Berrio 484.50      90  Camion Grande
    ## 164     1930      Ismael Rodero Monteagudo 482.50      60  Camion Grande
    ## 165      907       Fernando Mariano Berrio 226.75      60 Camion Pequeño
    ## 166      212        Hector Aragones Frutos  53.00      30          Panel
    ## 167     1387             Luis Jaime Urbano 346.75      90  Camion Grande
    ## 168      316                  Hector Giron  79.00      90          Panel
    ## 169      218                  Hector Giron  54.50      60          Panel
    ## 170      565                  Hector Giron 141.25      60 Camion Pequeño
    ## 171      893        Hector Aragones Frutos 223.25      90 Camion Pequeño
    ## 172      595              Felipe Villatoro 148.75      30 Camion Pequeño
    ## 173     1303             Luis Jaime Urbano 325.75      60  Camion Grande
    ## 174      303 Juan Francisco Portillo Gomez  75.75      90          Panel
    ## 175      703        Hector Aragones Frutos 175.75      30 Camion Pequeño
    ## 176     1149                  Hector Giron 287.25      60  Camion Grande
    ## 177      996          Pedro Alvarez Parejo 249.00      60 Camion Pequeño
    ## 178     1107        Hector Aragones Frutos 276.75      90  Camion Grande
    ## 179     1668              Felipe Villatoro 417.00      90  Camion Grande
    ## 180     1196              Felipe Villatoro 299.00      30  Camion Grande
    ## 181     1863 Juan Francisco Portillo Gomez 465.75      30  Camion Grande
    ## 182     1980          Angel Valdez Alegria 495.00      30  Camion Grande
    ## 183      419                  Hector Giron 104.75      90          Panel
    ## 184     1269          Angel Valdez Alegria 317.25      60  Camion Grande
    ## 185      304        Hector Aragones Frutos  76.00      90          Panel
    ## 186      625          Pedro Alvarez Parejo 156.25      90 Camion Pequeño
    ## 187     1073       Fernando Mariano Berrio 268.25      90  Camion Grande
    ## 188      541        Hector Aragones Frutos 135.25      90 Camion Pequeño
    ## 189      363              Felipe Villatoro  90.75      60          Panel
    ## 190      314 Juan Francisco Portillo Gomez  78.50      30          Panel
    ## 191      304       Fernando Mariano Berrio  76.00      30          Panel
    ## 192     1151             Luis Jaime Urbano 287.75      30  Camion Grande
    ## 193     1050      Ismael Rodero Monteagudo 262.50      60  Camion Grande
    ## 194     1723                  Hector Giron 430.75      60  Camion Grande
    ## 195     1305          Angel Valdez Alegria 326.25      60  Camion Grande
    ## 196      422        Hector Aragones Frutos 105.50      30          Panel
    ## 197     1641      Ismael Rodero Monteagudo 410.25      60  Camion Grande
    ## 198      386      Ismael Rodero Monteagudo  96.50      60          Panel
    ## 199     1079          Pedro Alvarez Parejo 269.75      60  Camion Grande
    ## 200      703      Ismael Rodero Monteagudo 175.75      30 Camion Pequeño
    ## 201      648      Ismael Rodero Monteagudo 162.00      30 Camion Pequeño
    ## 202     1730       Fernando Mariano Berrio 432.50      30  Camion Grande
    ## 203     1113             Luis Jaime Urbano 278.25      60  Camion Grande
    ## 204     1134 Juan Francisco Portillo Gomez 283.50      60  Camion Grande
    ## 205     1736 Juan Francisco Portillo Gomez 434.00      60  Camion Grande
    ## 206     1351 Juan Francisco Portillo Gomez 337.75      60  Camion Grande
    ## 207     1041              Felipe Villatoro 260.25      60  Camion Grande
    ## 208      397             Luis Jaime Urbano  99.25      30          Panel
    ## 209      988              Felipe Villatoro 247.00      60 Camion Pequeño
    ## 210      716          Angel Valdez Alegria 179.00      60 Camion Pequeño
    ## 211      459      Ismael Rodero Monteagudo 114.75      60          Panel
    ##     mes anio
    ## 1    07 2018
    ## 2    07 2018
    ## 3    07 2018
    ## 4    07 2018
    ## 5    07 2018
    ## 6    07 2018
    ## 7    07 2018
    ## 8    07 2018
    ## 9    07 2018
    ## 10   07 2018
    ## 11   07 2018
    ## 12   07 2018
    ## 13   07 2018
    ## 14   07 2018
    ## 15   07 2018
    ## 16   07 2018
    ## 17   07 2018
    ## 18   07 2018
    ## 19   07 2018
    ## 20   07 2018
    ## 21   07 2018
    ## 22   07 2018
    ## 23   07 2018
    ## 24   07 2018
    ## 25   07 2018
    ## 26   07 2018
    ## 27   07 2018
    ## 28   07 2018
    ## 29   07 2018
    ## 30   07 2018
    ## 31   07 2018
    ## 32   07 2018
    ## 33   07 2018
    ## 34   07 2018
    ## 35   07 2018
    ## 36   07 2018
    ## 37   07 2018
    ## 38   07 2018
    ## 39   07 2018
    ## 40   07 2018
    ## 41   07 2018
    ## 42   07 2018
    ## 43   07 2018
    ## 44   07 2018
    ## 45   07 2018
    ## 46   07 2018
    ## 47   07 2018
    ## 48   07 2018
    ## 49   07 2018
    ## 50   07 2018
    ## 51   07 2018
    ## 52   07 2018
    ## 53   07 2018
    ## 54   07 2018
    ## 55   07 2018
    ## 56   07 2018
    ## 57   07 2018
    ## 58   07 2018
    ## 59   07 2018
    ## 60   07 2018
    ## 61   07 2018
    ## 62   07 2018
    ## 63   07 2018
    ## 64   07 2018
    ## 65   07 2018
    ## 66   07 2018
    ## 67   07 2018
    ## 68   07 2018
    ## 69   07 2018
    ## 70   07 2018
    ## 71   07 2018
    ## 72   07 2018
    ## 73   07 2018
    ## 74   07 2018
    ## 75   07 2018
    ## 76   07 2018
    ## 77   07 2018
    ## 78   07 2018
    ## 79   07 2018
    ## 80   07 2018
    ## 81   07 2018
    ## 82   07 2018
    ## 83   07 2018
    ## 84   07 2018
    ## 85   07 2018
    ## 86   07 2018
    ## 87   07 2018
    ## 88   07 2018
    ## 89   07 2018
    ## 90   07 2018
    ## 91   07 2018
    ## 92   07 2018
    ## 93   07 2018
    ## 94   07 2018
    ## 95   07 2018
    ## 96   07 2018
    ## 97   07 2018
    ## 98   07 2018
    ## 99   07 2018
    ## 100  07 2018
    ## 101  07 2018
    ## 102  07 2018
    ## 103  07 2018
    ## 104  07 2018
    ## 105  07 2018
    ## 106  07 2018
    ## 107  07 2018
    ## 108  07 2018
    ## 109  07 2018
    ## 110  07 2018
    ## 111  07 2018
    ## 112  07 2018
    ## 113  07 2018
    ## 114  07 2018
    ## 115  07 2018
    ## 116  07 2018
    ## 117  07 2018
    ## 118  07 2018
    ## 119  07 2018
    ## 120  07 2018
    ## 121  07 2018
    ## 122  07 2018
    ## 123  07 2018
    ## 124  07 2018
    ## 125  07 2018
    ## 126  07 2018
    ## 127  07 2018
    ## 128  07 2018
    ## 129  07 2018
    ## 130  07 2018
    ## 131  07 2018
    ## 132  07 2018
    ## 133  07 2018
    ## 134  07 2018
    ## 135  07 2018
    ## 136  07 2018
    ## 137  07 2018
    ## 138  07 2018
    ## 139  07 2018
    ## 140  07 2018
    ## 141  07 2018
    ## 142  07 2018
    ## 143  07 2018
    ## 144  07 2018
    ## 145  07 2018
    ## 146  07 2018
    ## 147  07 2018
    ## 148  07 2018
    ## 149  07 2018
    ## 150  07 2018
    ## 151  07 2018
    ## 152  07 2018
    ## 153  07 2018
    ## 154  07 2018
    ## 155  07 2018
    ## 156  07 2018
    ## 157  07 2018
    ## 158  07 2018
    ## 159  07 2018
    ## 160  07 2018
    ## 161  07 2018
    ## 162  07 2018
    ## 163  07 2018
    ## 164  07 2018
    ## 165  07 2018
    ## 166  07 2018
    ## 167  07 2018
    ## 168  07 2018
    ## 169  07 2018
    ## 170  07 2018
    ## 171  07 2018
    ## 172  07 2018
    ## 173  07 2018
    ## 174  07 2018
    ## 175  07 2018
    ## 176  07 2018
    ## 177  07 2018
    ## 178  07 2018
    ## 179  07 2018
    ## 180  07 2018
    ## 181  07 2018
    ## 182  07 2018
    ## 183  07 2018
    ## 184  07 2018
    ## 185  07 2018
    ## 186  07 2018
    ## 187  07 2018
    ## 188  07 2018
    ## 189  07 2018
    ## 190  07 2018
    ## 191  07 2018
    ## 192  07 2018
    ## 193  07 2018
    ## 194  07 2018
    ## 195  07 2018
    ## 196  07 2018
    ## 197  07 2018
    ## 198  07 2018
    ## 199  07 2018
    ## 200  07 2018
    ## 201  07 2018
    ## 202  07 2018
    ## 203  07 2018
    ## 204  07 2018
    ## 205  07 2018
    ## 206  07 2018
    ## 207  07 2018
    ## 208  07 2018
    ## 209  07 2018
    ## 210  07 2018
    ## 211  07 2018
    ## 
    ## [[8]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10001397                EL GALLO NEGRO / Despacho a cliente     76001
    ## 2    10001398           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 3    10001399        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 4    10001400                            UBIQUO LABS |||FALTANTE     76002
    ## 5    10001401 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 6    10001402           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 7    10001403                  POLLO PINULITO/Despacho a cliente     76001
    ## 8    10001404                                     BAR LA OFICINA     76002
    ## 9    10001405                                TAQUERIA EL CHINITO     76001
    ## 10   10001406                  POLLO PINULITO/Despacho a cliente     76001
    ## 11   10001407                              HOSPITAL LAS AMERICAS     76001
    ## 12   10001408                EL GALLO NEGRO / Despacho a cliente     76001
    ## 13   10001409           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 14   10001410                                        UBIQUO LABS     76002
    ## 15   10001411      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 16   10001412                  POLLO PINULITO/Despacho a cliente     76002
    ## 17   10001413                     EL PINCHE OBELISCO |||Faltante     76002
    ## 18   10001414                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 19   10001415      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 20   10001416                EL GALLO NEGRO / Despacho a cliente     76001
    ## 21   10001417           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 22   10001418                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 23   10001419        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 24   10001420                                        UBIQUO LABS     76002
    ## 25   10001421                          POLLO PINULITO|||FALTANTE     76002
    ## 26   10001422           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 27   10001423                          POLLO PINULITO|||FALTANTE     76002
    ## 28   10001424                          POLLO PINULITO|||FALTANTE     76002
    ## 29   10001425           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 30   10001426                          POLLO PINULITO|||FALTANTE     76001
    ## 31   10001427            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 32   10001428                                     BAR LA OFICINA     76001
    ## 33   10001429                  POLLO PINULITO/Despacho a cliente     76001
    ## 34   10001430                                     BAR LA OFICINA     76001
    ## 35   10001431                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 36   10001432                          POLLO PINULITO|||FALTANTE     76002
    ## 37   10001433                            UBIQUO LABS |||FALTANTE     76002
    ## 38   10001434                  POLLO PINULITO/Despacho a cliente     76001
    ## 39   10001435                  POLLO PINULITO/Despacho a cliente     76001
    ## 40   10001436                                TAQUERIA EL CHINITO     76002
    ## 41   10001437      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 42   10001438                          POLLO PINULITO|||FALTANTE     76001
    ## 43   10001439                  POLLO PINULITO/Despacho a cliente     76002
    ## 44   10001440                          POLLO PINULITO|||FALTANTE     76002
    ## 45   10001441                            UBIQUO LABS |||FALTANTE     76002
    ## 46   10001442                  POLLO PINULITO/Despacho a cliente     76001
    ## 47   10001443           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 48   10001444 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 49   10001445                EL GALLO NEGRO / Despacho a cliente     76002
    ## 50   10001446                            UBIQUO LABS |||FALTANTE     76002
    ## 51   10001447           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 52   10001448        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 53   10001449            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 54   10001450            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 55   10001451                                        UBIQUO LABS     76001
    ## 56   10001452 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 57   10001453                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 58   10001454                              HOSPITAL LAS AMERICAS     76002
    ## 59   10001455                                     BAR LA OFICINA     76002
    ## 60   10001456                          POLLO PINULITO|||FALTANTE     76002
    ## 61   10001457           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 62   10001458                            UBIQUO LABS |||FALTANTE     76001
    ## 63   10001459      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 64   10001460            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 65   10001461                EL GALLO NEGRO / Despacho a cliente     76002
    ## 66   10001462 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 67   10001463           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 68   10001464                              HOSPITAL LAS AMERICAS     76002
    ## 69   10001465                EL GALLO NEGRO / Despacho a cliente     76002
    ## 70   10001466                          POLLO PINULITO|||FALTANTE     76002
    ## 71   10001467                                        UBIQUO LABS     76001
    ## 72   10001468            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 73   10001469                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 74   10001470                            UBIQUO LABS |||FALTANTE     76001
    ## 75   10001471 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 76   10001472 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 77   10001473                     EL PINCHE OBELISCO |||Faltante     76001
    ## 78   10001474                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 79   10001475                              HOSPITAL LAS AMERICAS     76002
    ## 80   10001476            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 81   10001477                          POLLO PINULITO|||FALTANTE     76001
    ## 82   10001478                     EL PINCHE OBELISCO |||Faltante     76001
    ## 83   10001479                EL GALLO NEGRO / Despacho a cliente     76001
    ## 84   10001480           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 85   10001481            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 86   10001482            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 87   10001483                     EL PINCHE OBELISCO |||Faltante     76001
    ## 88   10001484                     EL PINCHE OBELISCO |||Faltante     76002
    ## 89   10001485            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 90   10001486      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 91   10001487           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 92   10001488                EL GALLO NEGRO / Despacho a cliente     76001
    ## 93   10001489                                     BAR LA OFICINA     76001
    ## 94   10001490                                        UBIQUO LABS     76001
    ## 95   10001491                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 96   10001492                EL GALLO NEGRO / Despacho a cliente     76002
    ## 97   10001493                  POLLO PINULITO/Despacho a cliente     76001
    ## 98   10001494                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 99   10001495                     EL PINCHE OBELISCO |||Faltante     76001
    ## 100  10001496           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 101  10001497      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 102  10001498                                        UBIQUO LABS     76001
    ## 103  10001499                  POLLO PINULITO/Despacho a cliente     76001
    ## 104  10001500                     EL PINCHE OBELISCO |||Faltante     76002
    ## 105  10001501                              HOSPITAL LAS AMERICAS     76002
    ## 106  10001502        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 107  10001503        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 108  10001504        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 109  10001505        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 110  10001506                EL GALLO NEGRO / Despacho a cliente     76002
    ## 111  10001507      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 112  10001508           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 113  10001509        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 114  10001510      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 115  10001511            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 116  10001512            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 117  10001513           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 118  10001514                                     BAR LA OFICINA     76001
    ## 119  10001515      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 120  10001516            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 121  10001517                                TAQUERIA EL CHINITO     76001
    ## 122  10001518                EL GALLO NEGRO / Despacho a cliente     76002
    ## 123  10001519                                        UBIQUO LABS     76002
    ## 124  10001520                                        UBIQUO LABS     76002
    ## 125  10001521      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 126  10001522                              HOSPITAL LAS AMERICAS     76001
    ## 127  10001523                          POLLO PINULITO|||FALTANTE     76002
    ## 128  10001524                            UBIQUO LABS |||FALTANTE     76001
    ## 129  10001525                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 130  10001526           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 131  10001527                          POLLO PINULITO|||FALTANTE     76002
    ## 132  10001528            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 133  10001529            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 134  10001530                          POLLO PINULITO|||FALTANTE     76002
    ## 135  10001531      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 136  10001532                                     BAR LA OFICINA     76002
    ## 137  10001533            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 138  10001534                  POLLO PINULITO/Despacho a cliente     76001
    ## 139  10001535            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 140  10001536                            UBIQUO LABS |||FALTANTE     76001
    ## 141  10001537           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 142  10001538           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 143  10001539           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 144  10001540                EL GALLO NEGRO / Despacho a cliente     76001
    ## 145  10001541            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 146  10001542                  POLLO PINULITO/Despacho a cliente     76001
    ## 147  10001543      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 148  10001544                                        UBIQUO LABS     76001
    ## 149  10001545                                        UBIQUO LABS     76001
    ## 150  10001546            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 151  10001547                                TAQUERIA EL CHINITO     76001
    ## 152  10001548                              HOSPITAL LAS AMERICAS     76002
    ## 153  10001549            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 154  10001550                          POLLO PINULITO|||FALTANTE     76001
    ## 155  10001551                                     BAR LA OFICINA     76002
    ## 156  10001552           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 157  10001553                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 158  10001554                     EL PINCHE OBELISCO |||Faltante     76001
    ## 159  10001555 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 160  10001556            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 161  10001557           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 162  10001558            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 163  10001559        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 164  10001560                                TAQUERIA EL CHINITO     76001
    ## 165  10001561                            UBIQUO LABS |||FALTANTE     76002
    ## 166  10001562 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 167  10001563                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 168  10001564            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 169  10001565                                        UBIQUO LABS     76002
    ## 170  10001566 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 171  10001567                EL GALLO NEGRO / Despacho a cliente     76001
    ## 172  10001568                  POLLO PINULITO/Despacho a cliente     76001
    ## 173  10001569                                        UBIQUO LABS     76002
    ## 174  10001570                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 175  10001571      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 176  10001572                                        UBIQUO LABS     76001
    ## 177  10001573           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 178  10001574                                        UBIQUO LABS     76002
    ## 179  10001575                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 180  10001576                            UBIQUO LABS |||FALTANTE     76002
    ## 181  10001577                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 182  10001578                  POLLO PINULITO/Despacho a cliente     76001
    ## 183  10001579                            UBIQUO LABS |||FALTANTE     76001
    ## 184  10001580            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 185  10001581                EL GALLO NEGRO / Despacho a cliente     76002
    ## 186  10001582           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 187  10001583                            UBIQUO LABS |||FALTANTE     76001
    ## 188  10001584                  POLLO PINULITO/Despacho a cliente     76002
    ## 189  10001585                                     BAR LA OFICINA     76002
    ## 190  10001586      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 191  10001587                     EL PINCHE OBELISCO |||Faltante     76001
    ## 192  10001588                          POLLO PINULITO|||FALTANTE     76001
    ## 193  10001589           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 194  10001590                     EL PINCHE OBELISCO |||Faltante     76002
    ## 195  10001591                  POLLO PINULITO/Despacho a cliente     76002
    ## 196  10001592            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 197  10001593           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 198  10001594                EL GALLO NEGRO / Despacho a cliente     76001
    ## 199  10001595                       EL GALLO NEGRO |||DEVOLUCION     76002
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1362       Fernando Mariano Berrio 340.50      60  Camion Grande
    ## 2        879      Ismael Rodero Monteagudo 219.75      30 Camion Pequeño
    ## 3        661        Hector Aragones Frutos 165.25      30 Camion Pequeño
    ## 4       1520             Luis Jaime Urbano 380.00      30  Camion Grande
    ## 5        912          Pedro Alvarez Parejo 228.00      30 Camion Pequeño
    ## 6       1534                  Hector Giron 383.50      60  Camion Grande
    ## 7        565 Juan Francisco Portillo Gomez 141.25      30 Camion Pequeño
    ## 8       1332          Angel Valdez Alegria 333.00      60  Camion Grande
    ## 9       1725 Juan Francisco Portillo Gomez 431.25      30  Camion Grande
    ## 10      1824              Felipe Villatoro 456.00      60  Camion Grande
    ## 11       262              Felipe Villatoro  65.50      30          Panel
    ## 12       312       Fernando Mariano Berrio  78.00      30          Panel
    ## 13      1465      Ismael Rodero Monteagudo 366.25      90  Camion Grande
    ## 14      1095      Ismael Rodero Monteagudo 273.75      90  Camion Grande
    ## 15      1702      Ismael Rodero Monteagudo 425.50      60  Camion Grande
    ## 16      1985        Hector Aragones Frutos 496.25      90  Camion Grande
    ## 17       726                  Hector Giron 181.50      30 Camion Pequeño
    ## 18      1874      Ismael Rodero Monteagudo 468.50      30  Camion Grande
    ## 19       367      Ismael Rodero Monteagudo  91.75      30          Panel
    ## 20       347 Juan Francisco Portillo Gomez  86.75      30          Panel
    ## 21       454             Luis Jaime Urbano 113.50      30          Panel
    ## 22      1819 Juan Francisco Portillo Gomez 454.75      30  Camion Grande
    ## 23      1993 Juan Francisco Portillo Gomez 498.25      90  Camion Grande
    ## 24      1487      Ismael Rodero Monteagudo 371.75      90  Camion Grande
    ## 25      1102             Luis Jaime Urbano 275.50      30  Camion Grande
    ## 26       874          Pedro Alvarez Parejo 218.50      90 Camion Pequeño
    ## 27      1290          Pedro Alvarez Parejo 322.50      60  Camion Grande
    ## 28      1838                  Hector Giron 459.50      90  Camion Grande
    ## 29      1762      Ismael Rodero Monteagudo 440.50      90  Camion Grande
    ## 30       464      Ismael Rodero Monteagudo 116.00      90          Panel
    ## 31      1504             Luis Jaime Urbano 376.00      60  Camion Grande
    ## 32       424             Luis Jaime Urbano 106.00      90          Panel
    ## 33      1599                  Hector Giron 399.75      30  Camion Grande
    ## 34       399             Luis Jaime Urbano  99.75      30          Panel
    ## 35      1343 Juan Francisco Portillo Gomez 335.75      30  Camion Grande
    ## 36       587              Felipe Villatoro 146.75      60 Camion Pequeño
    ## 37      1839      Ismael Rodero Monteagudo 459.75      90  Camion Grande
    ## 38      1238        Hector Aragones Frutos 309.50      90  Camion Grande
    ## 39      1382                  Hector Giron 345.50      60  Camion Grande
    ## 40       654 Juan Francisco Portillo Gomez 163.50      60 Camion Pequeño
    ## 41       211          Pedro Alvarez Parejo  52.75      60          Panel
    ## 42       701          Pedro Alvarez Parejo 175.25      60 Camion Pequeño
    ## 43      1975              Felipe Villatoro 493.75      60  Camion Grande
    ## 44       389              Felipe Villatoro  97.25      60          Panel
    ## 45       324                  Hector Giron  81.00      90          Panel
    ## 46      1624 Juan Francisco Portillo Gomez 406.00      60  Camion Grande
    ## 47      1936              Felipe Villatoro 484.00      60  Camion Grande
    ## 48       996                  Hector Giron 249.00      60 Camion Pequeño
    ## 49       997             Luis Jaime Urbano 249.25      30 Camion Pequeño
    ## 50      1919              Felipe Villatoro 479.75      30  Camion Grande
    ## 51      1429                  Hector Giron 357.25      30  Camion Grande
    ## 52       885 Juan Francisco Portillo Gomez 221.25      30 Camion Pequeño
    ## 53      1429          Pedro Alvarez Parejo 357.25      30  Camion Grande
    ## 54      1682              Felipe Villatoro 420.50      30  Camion Grande
    ## 55      1361              Felipe Villatoro 340.25      90  Camion Grande
    ## 56      1559             Luis Jaime Urbano 389.75      60  Camion Grande
    ## 57       704 Juan Francisco Portillo Gomez 176.00      30 Camion Pequeño
    ## 58      1701                  Hector Giron 425.25      60  Camion Grande
    ## 59       654              Felipe Villatoro 163.50      30 Camion Pequeño
    ## 60      1458          Angel Valdez Alegria 364.50      30  Camion Grande
    ## 61       909                  Hector Giron 227.25      90 Camion Pequeño
    ## 62      1750          Angel Valdez Alegria 437.50      90  Camion Grande
    ## 63       819 Juan Francisco Portillo Gomez 204.75      60 Camion Pequeño
    ## 64      1496                  Hector Giron 374.00      30  Camion Grande
    ## 65      1256                  Hector Giron 314.00      30  Camion Grande
    ## 66      1454       Fernando Mariano Berrio 363.50      90  Camion Grande
    ## 67       270        Hector Aragones Frutos  67.50      90          Panel
    ## 68       534          Angel Valdez Alegria 133.50      90 Camion Pequeño
    ## 69      1674 Juan Francisco Portillo Gomez 418.50      30  Camion Grande
    ## 70       217                  Hector Giron  54.25      90          Panel
    ## 71      1546 Juan Francisco Portillo Gomez 386.50      30  Camion Grande
    ## 72      1750              Felipe Villatoro 437.50      30  Camion Grande
    ## 73      1017             Luis Jaime Urbano 254.25      90  Camion Grande
    ## 74       721 Juan Francisco Portillo Gomez 180.25      60 Camion Pequeño
    ## 75      1916             Luis Jaime Urbano 479.00      30  Camion Grande
    ## 76       506       Fernando Mariano Berrio 126.50      90 Camion Pequeño
    ## 77       574              Felipe Villatoro 143.50      30 Camion Pequeño
    ## 78      1386          Angel Valdez Alegria 346.50      90  Camion Grande
    ## 79       214          Pedro Alvarez Parejo  53.50      90          Panel
    ## 80      1955       Fernando Mariano Berrio 488.75      60  Camion Grande
    ## 81      1835       Fernando Mariano Berrio 458.75      60  Camion Grande
    ## 82       692              Felipe Villatoro 173.00      60 Camion Pequeño
    ## 83       650              Felipe Villatoro 162.50      90 Camion Pequeño
    ## 84       650 Juan Francisco Portillo Gomez 162.50      60 Camion Pequeño
    ## 85       875          Angel Valdez Alegria 218.75      30 Camion Pequeño
    ## 86      1263 Juan Francisco Portillo Gomez 315.75      90  Camion Grande
    ## 87       647                  Hector Giron 161.75      30 Camion Pequeño
    ## 88       579        Hector Aragones Frutos 144.75      30 Camion Pequeño
    ## 89       343 Juan Francisco Portillo Gomez  85.75      60          Panel
    ## 90       639      Ismael Rodero Monteagudo 159.75      30 Camion Pequeño
    ## 91      1325                  Hector Giron 331.25      30  Camion Grande
    ## 92       882      Ismael Rodero Monteagudo 220.50      30 Camion Pequeño
    ## 93       500        Hector Aragones Frutos 125.00      60          Panel
    ## 94       871      Ismael Rodero Monteagudo 217.75      60 Camion Pequeño
    ## 95      1438          Pedro Alvarez Parejo 359.50      60  Camion Grande
    ## 96       838                  Hector Giron 209.50      30 Camion Pequeño
    ## 97       519          Angel Valdez Alegria 129.75      90 Camion Pequeño
    ## 98       204              Felipe Villatoro  51.00      60          Panel
    ## 99      1347       Fernando Mariano Berrio 336.75      90  Camion Grande
    ## 100     1181      Ismael Rodero Monteagudo 295.25      90  Camion Grande
    ## 101     1184                  Hector Giron 296.00      60  Camion Grande
    ## 102      498 Juan Francisco Portillo Gomez 124.50      30          Panel
    ## 103      232        Hector Aragones Frutos  58.00      90          Panel
    ## 104     1175          Pedro Alvarez Parejo 293.75      60  Camion Grande
    ## 105      361          Angel Valdez Alegria  90.25      90          Panel
    ## 106     1793      Ismael Rodero Monteagudo 448.25      30  Camion Grande
    ## 107     1224      Ismael Rodero Monteagudo 306.00      90  Camion Grande
    ## 108     1572      Ismael Rodero Monteagudo 393.00      30  Camion Grande
    ## 109     1026          Pedro Alvarez Parejo 256.50      60  Camion Grande
    ## 110     1304          Pedro Alvarez Parejo 326.00      30  Camion Grande
    ## 111     1899          Pedro Alvarez Parejo 474.75      90  Camion Grande
    ## 112      945          Angel Valdez Alegria 236.25      30 Camion Pequeño
    ## 113      473              Felipe Villatoro 118.25      90          Panel
    ## 114     1149             Luis Jaime Urbano 287.25      60  Camion Grande
    ## 115      421                  Hector Giron 105.25      30          Panel
    ## 116      555             Luis Jaime Urbano 138.75      60 Camion Pequeño
    ## 117      374              Felipe Villatoro  93.50      90          Panel
    ## 118     1109          Pedro Alvarez Parejo 277.25      90  Camion Grande
    ## 119     1196       Fernando Mariano Berrio 299.00      90  Camion Grande
    ## 120      730       Fernando Mariano Berrio 182.50      30 Camion Pequeño
    ## 121     1914          Pedro Alvarez Parejo 478.50      60  Camion Grande
    ## 122      759        Hector Aragones Frutos 189.75      30 Camion Pequeño
    ## 123     1432 Juan Francisco Portillo Gomez 358.00      90  Camion Grande
    ## 124     1424                  Hector Giron 356.00      60  Camion Grande
    ## 125     1414 Juan Francisco Portillo Gomez 353.50      60  Camion Grande
    ## 126      504              Felipe Villatoro 126.00      90 Camion Pequeño
    ## 127      361              Felipe Villatoro  90.25      60          Panel
    ## 128     1141        Hector Aragones Frutos 285.25      90  Camion Grande
    ## 129     1985          Pedro Alvarez Parejo 496.25      90  Camion Grande
    ## 130     1599          Pedro Alvarez Parejo 399.75      30  Camion Grande
    ## 131      245             Luis Jaime Urbano  61.25      30          Panel
    ## 132      641        Hector Aragones Frutos 160.25      90 Camion Pequeño
    ## 133      680              Felipe Villatoro 170.00      30 Camion Pequeño
    ## 134      333          Pedro Alvarez Parejo  83.25      60          Panel
    ## 135     1037 Juan Francisco Portillo Gomez 259.25      30  Camion Grande
    ## 136     1946       Fernando Mariano Berrio 486.50      90  Camion Grande
    ## 137     1447                  Hector Giron 361.75      90  Camion Grande
    ## 138      282                  Hector Giron  70.50      30          Panel
    ## 139      590        Hector Aragones Frutos 147.50      30 Camion Pequeño
    ## 140      776       Fernando Mariano Berrio 194.00      30 Camion Pequeño
    ## 141      992              Felipe Villatoro 248.00      90 Camion Pequeño
    ## 142     1653      Ismael Rodero Monteagudo 413.25      60  Camion Grande
    ## 143     1874          Angel Valdez Alegria 468.50      90  Camion Grande
    ## 144      981          Angel Valdez Alegria 245.25      90 Camion Pequeño
    ## 145     1782          Angel Valdez Alegria 445.50      60  Camion Grande
    ## 146      514                  Hector Giron 128.50      30 Camion Pequeño
    ## 147      650          Angel Valdez Alegria 162.50      30 Camion Pequeño
    ## 148      874      Ismael Rodero Monteagudo 218.50      90 Camion Pequeño
    ## 149      583             Luis Jaime Urbano 145.75      60 Camion Pequeño
    ## 150      507             Luis Jaime Urbano 126.75      30 Camion Pequeño
    ## 151     1577       Fernando Mariano Berrio 394.25      90  Camion Grande
    ## 152     1290             Luis Jaime Urbano 322.50      90  Camion Grande
    ## 153     1601 Juan Francisco Portillo Gomez 400.25      60  Camion Grande
    ## 154     1689          Pedro Alvarez Parejo 422.25      60  Camion Grande
    ## 155      899        Hector Aragones Frutos 224.75      30 Camion Pequeño
    ## 156      845          Angel Valdez Alegria 211.25      90 Camion Pequeño
    ## 157     1628       Fernando Mariano Berrio 407.00      30  Camion Grande
    ## 158      413       Fernando Mariano Berrio 103.25      60          Panel
    ## 159     1832       Fernando Mariano Berrio 458.00      30  Camion Grande
    ## 160      884       Fernando Mariano Berrio 221.00      30 Camion Pequeño
    ## 161      516          Angel Valdez Alegria 129.00      90 Camion Pequeño
    ## 162      671             Luis Jaime Urbano 167.75      30 Camion Pequeño
    ## 163      573              Felipe Villatoro 143.25      90 Camion Pequeño
    ## 164     1622          Angel Valdez Alegria 405.50      60  Camion Grande
    ## 165      567          Pedro Alvarez Parejo 141.75      30 Camion Pequeño
    ## 166      288              Felipe Villatoro  72.00      60          Panel
    ## 167      686              Felipe Villatoro 171.50      90 Camion Pequeño
    ## 168      209              Felipe Villatoro  52.25      30          Panel
    ## 169     1760              Felipe Villatoro 440.00      30  Camion Grande
    ## 170      214      Ismael Rodero Monteagudo  53.50      90          Panel
    ## 171     1072              Felipe Villatoro 268.00      90  Camion Grande
    ## 172     1870        Hector Aragones Frutos 467.50      30  Camion Grande
    ## 173     1028          Pedro Alvarez Parejo 257.00      30  Camion Grande
    ## 174     1930 Juan Francisco Portillo Gomez 482.50      60  Camion Grande
    ## 175     1540          Angel Valdez Alegria 385.00      30  Camion Grande
    ## 176     1859              Felipe Villatoro 464.75      60  Camion Grande
    ## 177      527          Pedro Alvarez Parejo 131.75      90 Camion Pequeño
    ## 178      442          Angel Valdez Alegria 110.50      30          Panel
    ## 179     1086              Felipe Villatoro 271.50      60  Camion Grande
    ## 180      686          Pedro Alvarez Parejo 171.50      60 Camion Pequeño
    ## 181     1585      Ismael Rodero Monteagudo 396.25      60  Camion Grande
    ## 182      287       Fernando Mariano Berrio  71.75      30          Panel
    ## 183     1559        Hector Aragones Frutos 389.75      60  Camion Grande
    ## 184      877                  Hector Giron 219.25      30 Camion Pequeño
    ## 185      380        Hector Aragones Frutos  95.00      90          Panel
    ## 186      596        Hector Aragones Frutos 149.00      90 Camion Pequeño
    ## 187     1232              Felipe Villatoro 308.00      60  Camion Grande
    ## 188     1836                  Hector Giron 459.00      30  Camion Grande
    ## 189      594              Felipe Villatoro 148.50      30 Camion Pequeño
    ## 190     1969       Fernando Mariano Berrio 492.25      90  Camion Grande
    ## 191     1413       Fernando Mariano Berrio 353.25      60  Camion Grande
    ## 192     1126       Fernando Mariano Berrio 281.50      90  Camion Grande
    ## 193      248          Pedro Alvarez Parejo  62.00      90          Panel
    ## 194     1508       Fernando Mariano Berrio 377.00      30  Camion Grande
    ## 195     1555              Felipe Villatoro 388.75      60  Camion Grande
    ## 196     1526      Ismael Rodero Monteagudo 381.50      90  Camion Grande
    ## 197      907       Fernando Mariano Berrio 226.75      60 Camion Pequeño
    ## 198     1664      Ismael Rodero Monteagudo 416.00      30  Camion Grande
    ## 199      567       Fernando Mariano Berrio 141.75      60 Camion Pequeño
    ##     mes anio
    ## 1    08 2018
    ## 2    08 2018
    ## 3    08 2018
    ## 4    08 2018
    ## 5    08 2018
    ## 6    08 2018
    ## 7    08 2018
    ## 8    08 2018
    ## 9    08 2018
    ## 10   08 2018
    ## 11   08 2018
    ## 12   08 2018
    ## 13   08 2018
    ## 14   08 2018
    ## 15   08 2018
    ## 16   08 2018
    ## 17   08 2018
    ## 18   08 2018
    ## 19   08 2018
    ## 20   08 2018
    ## 21   08 2018
    ## 22   08 2018
    ## 23   08 2018
    ## 24   08 2018
    ## 25   08 2018
    ## 26   08 2018
    ## 27   08 2018
    ## 28   08 2018
    ## 29   08 2018
    ## 30   08 2018
    ## 31   08 2018
    ## 32   08 2018
    ## 33   08 2018
    ## 34   08 2018
    ## 35   08 2018
    ## 36   08 2018
    ## 37   08 2018
    ## 38   08 2018
    ## 39   08 2018
    ## 40   08 2018
    ## 41   08 2018
    ## 42   08 2018
    ## 43   08 2018
    ## 44   08 2018
    ## 45   08 2018
    ## 46   08 2018
    ## 47   08 2018
    ## 48   08 2018
    ## 49   08 2018
    ## 50   08 2018
    ## 51   08 2018
    ## 52   08 2018
    ## 53   08 2018
    ## 54   08 2018
    ## 55   08 2018
    ## 56   08 2018
    ## 57   08 2018
    ## 58   08 2018
    ## 59   08 2018
    ## 60   08 2018
    ## 61   08 2018
    ## 62   08 2018
    ## 63   08 2018
    ## 64   08 2018
    ## 65   08 2018
    ## 66   08 2018
    ## 67   08 2018
    ## 68   08 2018
    ## 69   08 2018
    ## 70   08 2018
    ## 71   08 2018
    ## 72   08 2018
    ## 73   08 2018
    ## 74   08 2018
    ## 75   08 2018
    ## 76   08 2018
    ## 77   08 2018
    ## 78   08 2018
    ## 79   08 2018
    ## 80   08 2018
    ## 81   08 2018
    ## 82   08 2018
    ## 83   08 2018
    ## 84   08 2018
    ## 85   08 2018
    ## 86   08 2018
    ## 87   08 2018
    ## 88   08 2018
    ## 89   08 2018
    ## 90   08 2018
    ## 91   08 2018
    ## 92   08 2018
    ## 93   08 2018
    ## 94   08 2018
    ## 95   08 2018
    ## 96   08 2018
    ## 97   08 2018
    ## 98   08 2018
    ## 99   08 2018
    ## 100  08 2018
    ## 101  08 2018
    ## 102  08 2018
    ## 103  08 2018
    ## 104  08 2018
    ## 105  08 2018
    ## 106  08 2018
    ## 107  08 2018
    ## 108  08 2018
    ## 109  08 2018
    ## 110  08 2018
    ## 111  08 2018
    ## 112  08 2018
    ## 113  08 2018
    ## 114  08 2018
    ## 115  08 2018
    ## 116  08 2018
    ## 117  08 2018
    ## 118  08 2018
    ## 119  08 2018
    ## 120  08 2018
    ## 121  08 2018
    ## 122  08 2018
    ## 123  08 2018
    ## 124  08 2018
    ## 125  08 2018
    ## 126  08 2018
    ## 127  08 2018
    ## 128  08 2018
    ## 129  08 2018
    ## 130  08 2018
    ## 131  08 2018
    ## 132  08 2018
    ## 133  08 2018
    ## 134  08 2018
    ## 135  08 2018
    ## 136  08 2018
    ## 137  08 2018
    ## 138  08 2018
    ## 139  08 2018
    ## 140  08 2018
    ## 141  08 2018
    ## 142  08 2018
    ## 143  08 2018
    ## 144  08 2018
    ## 145  08 2018
    ## 146  08 2018
    ## 147  08 2018
    ## 148  08 2018
    ## 149  08 2018
    ## 150  08 2018
    ## 151  08 2018
    ## 152  08 2018
    ## 153  08 2018
    ## 154  08 2018
    ## 155  08 2018
    ## 156  08 2018
    ## 157  08 2018
    ## 158  08 2018
    ## 159  08 2018
    ## 160  08 2018
    ## 161  08 2018
    ## 162  08 2018
    ## 163  08 2018
    ## 164  08 2018
    ## 165  08 2018
    ## 166  08 2018
    ## 167  08 2018
    ## 168  08 2018
    ## 169  08 2018
    ## 170  08 2018
    ## 171  08 2018
    ## 172  08 2018
    ## 173  08 2018
    ## 174  08 2018
    ## 175  08 2018
    ## 176  08 2018
    ## 177  08 2018
    ## 178  08 2018
    ## 179  08 2018
    ## 180  08 2018
    ## 181  08 2018
    ## 182  08 2018
    ## 183  08 2018
    ## 184  08 2018
    ## 185  08 2018
    ## 186  08 2018
    ## 187  08 2018
    ## 188  08 2018
    ## 189  08 2018
    ## 190  08 2018
    ## 191  08 2018
    ## 192  08 2018
    ## 193  08 2018
    ## 194  08 2018
    ## 195  08 2018
    ## 196  08 2018
    ## 197  08 2018
    ## 198  08 2018
    ## 199  08 2018
    ## 
    ## [[9]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10001596                                     BAR LA OFICINA     76002
    ## 2    10001597                EL GALLO NEGRO / Despacho a cliente     76002
    ## 3    10001598                              HOSPITAL LAS AMERICAS     76001
    ## 4    10001599                  POLLO PINULITO/Despacho a cliente     76002
    ## 5    10001600            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 6    10001601                  POLLO PINULITO/Despacho a cliente     76002
    ## 7    10001602                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 8    10001603                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 9    10001604                                TAQUERIA EL CHINITO     76002
    ## 10   10001605                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 11   10001606 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 12   10001607                     EL PINCHE OBELISCO |||Faltante     76001
    ## 13   10001608                EL GALLO NEGRO / Despacho a cliente     76001
    ## 14   10001609                                     BAR LA OFICINA     76002
    ## 15   10001610            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 16   10001611            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 17   10001612                          POLLO PINULITO|||FALTANTE     76001
    ## 18   10001613                  POLLO PINULITO/Despacho a cliente     76001
    ## 19   10001614                                     BAR LA OFICINA     76002
    ## 20   10001615      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 21   10001616                                        UBIQUO LABS     76001
    ## 22   10001617                     EL PINCHE OBELISCO |||Faltante     76002
    ## 23   10001618                            UBIQUO LABS |||FALTANTE     76002
    ## 24   10001619                              HOSPITAL LAS AMERICAS     76002
    ## 25   10001620                     EL PINCHE OBELISCO |||Faltante     76002
    ## 26   10001621        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 27   10001622                                        UBIQUO LABS     76002
    ## 28   10001623                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 29   10001624                     EL PINCHE OBELISCO |||Faltante     76001
    ## 30   10001625           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 31   10001626                     EL PINCHE OBELISCO |||Faltante     76001
    ## 32   10001627                  POLLO PINULITO/Despacho a cliente     76001
    ## 33   10001628           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 34   10001629                          POLLO PINULITO|||FALTANTE     76002
    ## 35   10001630                            UBIQUO LABS |||FALTANTE     76002
    ## 36   10001631                     EL PINCHE OBELISCO |||Faltante     76002
    ## 37   10001632                            UBIQUO LABS |||FALTANTE     76001
    ## 38   10001633                              HOSPITAL LAS AMERICAS     76001
    ## 39   10001634                                        UBIQUO LABS     76001
    ## 40   10001635                  POLLO PINULITO/Despacho a cliente     76002
    ## 41   10001636      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 42   10001637                                TAQUERIA EL CHINITO     76001
    ## 43   10001638           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 44   10001639                          POLLO PINULITO|||FALTANTE     76001
    ## 45   10001640                                        UBIQUO LABS     76002
    ## 46   10001641        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 47   10001642        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 48   10001643                            UBIQUO LABS |||FALTANTE     76002
    ## 49   10001644                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 50   10001645                     EL PINCHE OBELISCO |||Faltante     76001
    ## 51   10001646                EL GALLO NEGRO / Despacho a cliente     76001
    ## 52   10001647                  POLLO PINULITO/Despacho a cliente     76001
    ## 53   10001648           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 54   10001649                          POLLO PINULITO|||FALTANTE     76002
    ## 55   10001650 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 56   10001651                                     BAR LA OFICINA     76001
    ## 57   10001652           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 58   10001653                EL GALLO NEGRO / Despacho a cliente     76002
    ## 59   10001654 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 60   10001655            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 61   10001656                     EL PINCHE OBELISCO |||Faltante     76001
    ## 62   10001657 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 63   10001658           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 64   10001659                              HOSPITAL LAS AMERICAS     76002
    ## 65   10001660           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 66   10001661                                        UBIQUO LABS     76002
    ## 67   10001662                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 68   10001663            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 69   10001664                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 70   10001665                            UBIQUO LABS |||FALTANTE     76001
    ## 71   10001666                          POLLO PINULITO|||FALTANTE     76002
    ## 72   10001667        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 73   10001668                          POLLO PINULITO|||FALTANTE     76001
    ## 74   10001669                              HOSPITAL LAS AMERICAS     76002
    ## 75   10001670                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 76   10001671        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 77   10001672      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 78   10001673           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 79   10001674        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 80   10001675           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 81   10001676                  POLLO PINULITO/Despacho a cliente     76001
    ## 82   10001677                                TAQUERIA EL CHINITO     76001
    ## 83   10001678                          POLLO PINULITO|||FALTANTE     76002
    ## 84   10001679           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 85   10001680                  POLLO PINULITO/Despacho a cliente     76001
    ## 86   10001681           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 87   10001682                     EL PINCHE OBELISCO |||Faltante     76001
    ## 88   10001683        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 89   10001684           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 90   10001685           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 91   10001686            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 92   10001687           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 93   10001688                                TAQUERIA EL CHINITO     76002
    ## 94   10001689                                TAQUERIA EL CHINITO     76001
    ## 95   10001690           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 96   10001691                            UBIQUO LABS |||FALTANTE     76002
    ## 97   10001692        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 98   10001693            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 99   10001694                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 100  10001695                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 101  10001696                                        UBIQUO LABS     76002
    ## 102  10001697                                     BAR LA OFICINA     76002
    ## 103  10001698                  POLLO PINULITO/Despacho a cliente     76001
    ## 104  10001699                                     BAR LA OFICINA     76002
    ## 105  10001700                                     BAR LA OFICINA     76001
    ## 106  10001701           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 107  10001702                                        UBIQUO LABS     76001
    ## 108  10001703                                TAQUERIA EL CHINITO     76002
    ## 109  10001704                EL GALLO NEGRO / Despacho a cliente     76002
    ## 110  10001705                     EL PINCHE OBELISCO |||Faltante     76002
    ## 111  10001706                                     BAR LA OFICINA     76002
    ## 112  10001707            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 113  10001708      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 114  10001709                              HOSPITAL LAS AMERICAS     76002
    ## 115  10001710                          POLLO PINULITO|||FALTANTE     76002
    ## 116  10001711                              HOSPITAL LAS AMERICAS     76001
    ## 117  10001712                          POLLO PINULITO|||FALTANTE     76001
    ## 118  10001713 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 119  10001714                          POLLO PINULITO|||FALTANTE     76002
    ## 120  10001715                                        UBIQUO LABS     76001
    ## 121  10001716                                TAQUERIA EL CHINITO     76001
    ## 122  10001717        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 123  10001718            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 124  10001719                                        UBIQUO LABS     76002
    ## 125  10001720           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 126  10001721 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 127  10001722                              HOSPITAL LAS AMERICAS     76002
    ## 128  10001723                     EL PINCHE OBELISCO |||Faltante     76001
    ## 129  10001724                                        UBIQUO LABS     76001
    ## 130  10001725                EL GALLO NEGRO / Despacho a cliente     76001
    ## 131  10001726           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 132  10001727                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 133  10001728                                TAQUERIA EL CHINITO     76002
    ## 134  10001729      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 135  10001730                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 136  10001731           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 137  10001732            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 138  10001733           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 139  10001734                          POLLO PINULITO|||FALTANTE     76002
    ## 140  10001735                EL GALLO NEGRO / Despacho a cliente     76001
    ## 141  10001736                          POLLO PINULITO|||FALTANTE     76002
    ## 142  10001737                          POLLO PINULITO|||FALTANTE     76001
    ## 143  10001738           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 144  10001739        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 145  10001740        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 146  10001741                                     BAR LA OFICINA     76001
    ## 147  10001742            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 148  10001743      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 149  10001744        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 150  10001745        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 151  10001746                                TAQUERIA EL CHINITO     76002
    ## 152  10001747            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 153  10001748                          POLLO PINULITO|||FALTANTE     76002
    ## 154  10001749           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 155  10001750                     EL PINCHE OBELISCO |||Faltante     76001
    ## 156  10001751                            UBIQUO LABS |||FALTANTE     76001
    ## 157  10001752                          POLLO PINULITO|||FALTANTE     76001
    ## 158  10001753        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 159  10001754                     EL PINCHE OBELISCO |||Faltante     76002
    ## 160  10001755                     EL PINCHE OBELISCO |||Faltante     76001
    ## 161  10001756                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 162  10001757                                TAQUERIA EL CHINITO     76002
    ## 163  10001758            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 164  10001759      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 165  10001760 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 166  10001761                          POLLO PINULITO|||FALTANTE     76001
    ## 167  10001762                              HOSPITAL LAS AMERICAS     76001
    ## 168  10001763           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 169  10001764                                        UBIQUO LABS     76002
    ## 170  10001765                            UBIQUO LABS |||FALTANTE     76002
    ## 171  10001766        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 172  10001767 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 173  10001768           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 174  10001769      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 175  10001770                              HOSPITAL LAS AMERICAS     76001
    ## 176  10001771                                TAQUERIA EL CHINITO     76001
    ## 177  10001772 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 178  10001773 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 179  10001774                          POLLO PINULITO|||FALTANTE     76002
    ## 180  10001775 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 181  10001776            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 182  10001777                  POLLO PINULITO/Despacho a cliente     76002
    ## 183  10001778                EL GALLO NEGRO / Despacho a cliente     76001
    ## 184  10001779                                TAQUERIA EL CHINITO     76001
    ## 185  10001780                                        UBIQUO LABS     76002
    ## 186  10001781                EL GALLO NEGRO / Despacho a cliente     76002
    ## 187  10001782                                TAQUERIA EL CHINITO     76002
    ## 188  10001783                                        UBIQUO LABS     76002
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1617             Luis Jaime Urbano 404.25      90  Camion Grande
    ## 2       1407              Felipe Villatoro 351.75      90  Camion Grande
    ## 3       1006      Ismael Rodero Monteagudo 251.50      90  Camion Grande
    ## 4       1768        Hector Aragones Frutos 442.00      60  Camion Grande
    ## 5       1989        Hector Aragones Frutos 497.25      60  Camion Grande
    ## 6        784              Felipe Villatoro 196.00      30 Camion Pequeño
    ## 7       1499        Hector Aragones Frutos 374.75      90  Camion Grande
    ## 8        714             Luis Jaime Urbano 178.50      30 Camion Pequeño
    ## 9        704                  Hector Giron 176.00      90 Camion Pequeño
    ## 10       720        Hector Aragones Frutos 180.00      90 Camion Pequeño
    ## 11      1537              Felipe Villatoro 384.25      30  Camion Grande
    ## 12       869              Felipe Villatoro 217.25      90 Camion Pequeño
    ## 13      1974        Hector Aragones Frutos 493.50      90  Camion Grande
    ## 14       686             Luis Jaime Urbano 171.50      90 Camion Pequeño
    ## 15      1364          Angel Valdez Alegria 341.00      30  Camion Grande
    ## 16      1204      Ismael Rodero Monteagudo 301.00      90  Camion Grande
    ## 17      1466      Ismael Rodero Monteagudo 366.50      30  Camion Grande
    ## 18      1646      Ismael Rodero Monteagudo 411.50      30  Camion Grande
    ## 19       696        Hector Aragones Frutos 174.00      30 Camion Pequeño
    ## 20       761          Angel Valdez Alegria 190.25      60 Camion Pequeño
    ## 21       326          Pedro Alvarez Parejo  81.50      90          Panel
    ## 22      1672      Ismael Rodero Monteagudo 418.00      30  Camion Grande
    ## 23      1803                  Hector Giron 450.75      60  Camion Grande
    ## 24      1036          Angel Valdez Alegria 259.00      90  Camion Grande
    ## 25      1729        Hector Aragones Frutos 432.25      60  Camion Grande
    ## 26       640        Hector Aragones Frutos 160.00      30 Camion Pequeño
    ## 27       768          Pedro Alvarez Parejo 192.00      30 Camion Pequeño
    ## 28      1401      Ismael Rodero Monteagudo 350.25      90  Camion Grande
    ## 29      1138             Luis Jaime Urbano 284.50      30  Camion Grande
    ## 30       492             Luis Jaime Urbano 123.00      90          Panel
    ## 31      1524          Angel Valdez Alegria 381.00      30  Camion Grande
    ## 32      1688             Luis Jaime Urbano 422.00      60  Camion Grande
    ## 33      1183        Hector Aragones Frutos 295.75      30  Camion Grande
    ## 34      1004       Fernando Mariano Berrio 251.00      90  Camion Grande
    ## 35       319          Pedro Alvarez Parejo  79.75      90          Panel
    ## 36       360      Ismael Rodero Monteagudo  90.00      90          Panel
    ## 37       257        Hector Aragones Frutos  64.25      90          Panel
    ## 38       297 Juan Francisco Portillo Gomez  74.25      30          Panel
    ## 39       269          Pedro Alvarez Parejo  67.25      60          Panel
    ## 40       242          Angel Valdez Alegria  60.50      60          Panel
    ## 41       957       Fernando Mariano Berrio 239.25      30 Camion Pequeño
    ## 42      1198        Hector Aragones Frutos 299.50      30  Camion Grande
    ## 43      1454       Fernando Mariano Berrio 363.50      90  Camion Grande
    ## 44      1963          Angel Valdez Alegria 490.75      30  Camion Grande
    ## 45      1522                  Hector Giron 380.50      60  Camion Grande
    ## 46      1261          Pedro Alvarez Parejo 315.25      90  Camion Grande
    ## 47       660             Luis Jaime Urbano 165.00      90 Camion Pequeño
    ## 48      1585       Fernando Mariano Berrio 396.25      30  Camion Grande
    ## 49      1725      Ismael Rodero Monteagudo 431.25      90  Camion Grande
    ## 50       843 Juan Francisco Portillo Gomez 210.75      60 Camion Pequeño
    ## 51      1126          Pedro Alvarez Parejo 281.50      30  Camion Grande
    ## 52       883        Hector Aragones Frutos 220.75      30 Camion Pequeño
    ## 53       255          Angel Valdez Alegria  63.75      30          Panel
    ## 54       409          Pedro Alvarez Parejo 102.25      90          Panel
    ## 55      1793             Luis Jaime Urbano 448.25      30  Camion Grande
    ## 56       984        Hector Aragones Frutos 246.00      30 Camion Pequeño
    ## 57       245          Pedro Alvarez Parejo  61.25      30          Panel
    ## 58      1113 Juan Francisco Portillo Gomez 278.25      60  Camion Grande
    ## 59      1278       Fernando Mariano Berrio 319.50      60  Camion Grande
    ## 60       531                  Hector Giron 132.75      90 Camion Pequeño
    ## 61       941             Luis Jaime Urbano 235.25      30 Camion Pequeño
    ## 62       911          Pedro Alvarez Parejo 227.75      30 Camion Pequeño
    ## 63       342                  Hector Giron  85.50      30          Panel
    ## 64      1957        Hector Aragones Frutos 489.25      90  Camion Grande
    ## 65       514                  Hector Giron 128.50      60 Camion Pequeño
    ## 66       636             Luis Jaime Urbano 159.00      60 Camion Pequeño
    ## 67       563          Angel Valdez Alegria 140.75      90 Camion Pequeño
    ## 68      1346          Pedro Alvarez Parejo 336.50      30  Camion Grande
    ## 69       805          Angel Valdez Alegria 201.25      60 Camion Pequeño
    ## 70       217        Hector Aragones Frutos  54.25      90          Panel
    ## 71       901        Hector Aragones Frutos 225.25      30 Camion Pequeño
    ## 72       491              Felipe Villatoro 122.75      90          Panel
    ## 73      1723          Angel Valdez Alegria 430.75      90  Camion Grande
    ## 74      1209       Fernando Mariano Berrio 302.25      60  Camion Grande
    ## 75      1565        Hector Aragones Frutos 391.25      90  Camion Grande
    ## 76      1866 Juan Francisco Portillo Gomez 466.50      30  Camion Grande
    ## 77      1589              Felipe Villatoro 397.25      90  Camion Grande
    ## 78       763             Luis Jaime Urbano 190.75      30 Camion Pequeño
    ## 79      1517          Pedro Alvarez Parejo 379.25      30  Camion Grande
    ## 80      1140          Angel Valdez Alegria 285.00      90  Camion Grande
    ## 81      1822          Pedro Alvarez Parejo 455.50      90  Camion Grande
    ## 82       653              Felipe Villatoro 163.25      30 Camion Pequeño
    ## 83       465       Fernando Mariano Berrio 116.25      30          Panel
    ## 84      1776                  Hector Giron 444.00      90  Camion Grande
    ## 85      1211             Luis Jaime Urbano 302.75      60  Camion Grande
    ## 86       352        Hector Aragones Frutos  88.00      90          Panel
    ## 87       590       Fernando Mariano Berrio 147.50      90 Camion Pequeño
    ## 88      1728                  Hector Giron 432.00      60  Camion Grande
    ## 89      1240       Fernando Mariano Berrio 310.00      90  Camion Grande
    ## 90      1832             Luis Jaime Urbano 458.00      60  Camion Grande
    ## 91       545          Angel Valdez Alegria 136.25      60 Camion Pequeño
    ## 92      1695          Pedro Alvarez Parejo 423.75      60  Camion Grande
    ## 93       643       Fernando Mariano Berrio 160.75      30 Camion Pequeño
    ## 94       427          Angel Valdez Alegria 106.75      60          Panel
    ## 95      1694          Pedro Alvarez Parejo 423.50      30  Camion Grande
    ## 96      1083                  Hector Giron 270.75      60  Camion Grande
    ## 97      1669       Fernando Mariano Berrio 417.25      60  Camion Grande
    ## 98      1169        Hector Aragones Frutos 292.25      30  Camion Grande
    ## 99      1853 Juan Francisco Portillo Gomez 463.25      30  Camion Grande
    ## 100     1844        Hector Aragones Frutos 461.00      30  Camion Grande
    ## 101     1740              Felipe Villatoro 435.00      60  Camion Grande
    ## 102     1834             Luis Jaime Urbano 458.50      60  Camion Grande
    ## 103      276      Ismael Rodero Monteagudo  69.00      30          Panel
    ## 104      241       Fernando Mariano Berrio  60.25      30          Panel
    ## 105     1492          Angel Valdez Alegria 373.00      30  Camion Grande
    ## 106      782        Hector Aragones Frutos 195.50      30 Camion Pequeño
    ## 107     1680          Angel Valdez Alegria 420.00      90  Camion Grande
    ## 108      292                  Hector Giron  73.00      90          Panel
    ## 109      904        Hector Aragones Frutos 226.00      30 Camion Pequeño
    ## 110      572                  Hector Giron 143.00      90 Camion Pequeño
    ## 111      680        Hector Aragones Frutos 170.00      60 Camion Pequeño
    ## 112     1339              Felipe Villatoro 334.75      30  Camion Grande
    ## 113     1133      Ismael Rodero Monteagudo 283.25      60  Camion Grande
    ## 114      557             Luis Jaime Urbano 139.25      30 Camion Pequeño
    ## 115     1943       Fernando Mariano Berrio 485.75      30  Camion Grande
    ## 116      432       Fernando Mariano Berrio 108.00      60          Panel
    ## 117     1990                  Hector Giron 497.50      30  Camion Grande
    ## 118      814 Juan Francisco Portillo Gomez 203.50      30 Camion Pequeño
    ## 119      998        Hector Aragones Frutos 249.50      60 Camion Pequeño
    ## 120     1094             Luis Jaime Urbano 273.50      30  Camion Grande
    ## 121     1624          Pedro Alvarez Parejo 406.00      30  Camion Grande
    ## 122     1117 Juan Francisco Portillo Gomez 279.25      30  Camion Grande
    ## 123     1720             Luis Jaime Urbano 430.00      90  Camion Grande
    ## 124      892          Pedro Alvarez Parejo 223.00      90 Camion Pequeño
    ## 125     1089              Felipe Villatoro 272.25      60  Camion Grande
    ## 126     1949       Fernando Mariano Berrio 487.25      30  Camion Grande
    ## 127     1632      Ismael Rodero Monteagudo 408.00      30  Camion Grande
    ## 128     1273        Hector Aragones Frutos 318.25      30  Camion Grande
    ## 129      955      Ismael Rodero Monteagudo 238.75      30 Camion Pequeño
    ## 130      822          Pedro Alvarez Parejo 205.50      30 Camion Pequeño
    ## 131      522          Pedro Alvarez Parejo 130.50      90 Camion Pequeño
    ## 132     1372 Juan Francisco Portillo Gomez 343.00      90  Camion Grande
    ## 133      700              Felipe Villatoro 175.00      30 Camion Pequeño
    ## 134     1247          Pedro Alvarez Parejo 311.75      90  Camion Grande
    ## 135     1940          Pedro Alvarez Parejo 485.00      60  Camion Grande
    ## 136      700              Felipe Villatoro 175.00      30 Camion Pequeño
    ## 137     1891          Pedro Alvarez Parejo 472.75      30  Camion Grande
    ## 138     1297 Juan Francisco Portillo Gomez 324.25      90  Camion Grande
    ## 139      275        Hector Aragones Frutos  68.75      30          Panel
    ## 140      325             Luis Jaime Urbano  81.25      30          Panel
    ## 141     1706              Felipe Villatoro 426.50      30  Camion Grande
    ## 142      553             Luis Jaime Urbano 138.25      90 Camion Pequeño
    ## 143      429             Luis Jaime Urbano 107.25      30          Panel
    ## 144     1416          Angel Valdez Alegria 354.00      90  Camion Grande
    ## 145     1138        Hector Aragones Frutos 284.50      60  Camion Grande
    ## 146      332          Angel Valdez Alegria  83.00      60          Panel
    ## 147      435          Pedro Alvarez Parejo 108.75      60          Panel
    ## 148     1330 Juan Francisco Portillo Gomez 332.50      60  Camion Grande
    ## 149     1911                  Hector Giron 477.75      90  Camion Grande
    ## 150      429                  Hector Giron 107.25      60          Panel
    ## 151     1711      Ismael Rodero Monteagudo 427.75      90  Camion Grande
    ## 152      855              Felipe Villatoro 213.75      90 Camion Pequeño
    ## 153     1443                  Hector Giron 360.75      90  Camion Grande
    ## 154      594             Luis Jaime Urbano 148.50      90 Camion Pequeño
    ## 155      671       Fernando Mariano Berrio 167.75      30 Camion Pequeño
    ## 156      250       Fernando Mariano Berrio  62.50      30          Panel
    ## 157     1515             Luis Jaime Urbano 378.75      60  Camion Grande
    ## 158      526                  Hector Giron 131.50      30 Camion Pequeño
    ## 159      451          Angel Valdez Alegria 112.75      30          Panel
    ## 160     1255       Fernando Mariano Berrio 313.75      60  Camion Grande
    ## 161      907          Angel Valdez Alegria 226.75      90 Camion Pequeño
    ## 162     1959                  Hector Giron 489.75      90  Camion Grande
    ## 163      844          Angel Valdez Alegria 211.00      90 Camion Pequeño
    ## 164      815             Luis Jaime Urbano 203.75      60 Camion Pequeño
    ## 165     1929       Fernando Mariano Berrio 482.25      60  Camion Grande
    ## 166     1233          Pedro Alvarez Parejo 308.25      60  Camion Grande
    ## 167      328          Pedro Alvarez Parejo  82.00      90          Panel
    ## 168     1224              Felipe Villatoro 306.00      30  Camion Grande
    ## 169     1186 Juan Francisco Portillo Gomez 296.50      90  Camion Grande
    ## 170     1945 Juan Francisco Portillo Gomez 486.25      30  Camion Grande
    ## 171     1464       Fernando Mariano Berrio 366.00      90  Camion Grande
    ## 172     1383        Hector Aragones Frutos 345.75      60  Camion Grande
    ## 173      641                  Hector Giron 160.25      90 Camion Pequeño
    ## 174      430       Fernando Mariano Berrio 107.50      60          Panel
    ## 175     1741                  Hector Giron 435.25      30  Camion Grande
    ## 176     1820              Felipe Villatoro 455.00      60  Camion Grande
    ## 177     1555              Felipe Villatoro 388.75      30  Camion Grande
    ## 178     1754      Ismael Rodero Monteagudo 438.50      30  Camion Grande
    ## 179     1473      Ismael Rodero Monteagudo 368.25      30  Camion Grande
    ## 180     1632                  Hector Giron 408.00      30  Camion Grande
    ## 181     1470                  Hector Giron 367.50      90  Camion Grande
    ## 182     1562 Juan Francisco Portillo Gomez 390.50      60  Camion Grande
    ## 183      293 Juan Francisco Portillo Gomez  73.25      30          Panel
    ## 184     1053          Angel Valdez Alegria 263.25      30  Camion Grande
    ## 185      525          Angel Valdez Alegria 131.25      60 Camion Pequeño
    ## 186      618                  Hector Giron 154.50      30 Camion Pequeño
    ## 187      654      Ismael Rodero Monteagudo 163.50      30 Camion Pequeño
    ## 188      923                  Hector Giron 230.75      60 Camion Pequeño
    ##     mes anio
    ## 1    09 2018
    ## 2    09 2018
    ## 3    09 2018
    ## 4    09 2018
    ## 5    09 2018
    ## 6    09 2018
    ## 7    09 2018
    ## 8    09 2018
    ## 9    09 2018
    ## 10   09 2018
    ## 11   09 2018
    ## 12   09 2018
    ## 13   09 2018
    ## 14   09 2018
    ## 15   09 2018
    ## 16   09 2018
    ## 17   09 2018
    ## 18   09 2018
    ## 19   09 2018
    ## 20   09 2018
    ## 21   09 2018
    ## 22   09 2018
    ## 23   09 2018
    ## 24   09 2018
    ## 25   09 2018
    ## 26   09 2018
    ## 27   09 2018
    ## 28   09 2018
    ## 29   09 2018
    ## 30   09 2018
    ## 31   09 2018
    ## 32   09 2018
    ## 33   09 2018
    ## 34   09 2018
    ## 35   09 2018
    ## 36   09 2018
    ## 37   09 2018
    ## 38   09 2018
    ## 39   09 2018
    ## 40   09 2018
    ## 41   09 2018
    ## 42   09 2018
    ## 43   09 2018
    ## 44   09 2018
    ## 45   09 2018
    ## 46   09 2018
    ## 47   09 2018
    ## 48   09 2018
    ## 49   09 2018
    ## 50   09 2018
    ## 51   09 2018
    ## 52   09 2018
    ## 53   09 2018
    ## 54   09 2018
    ## 55   09 2018
    ## 56   09 2018
    ## 57   09 2018
    ## 58   09 2018
    ## 59   09 2018
    ## 60   09 2018
    ## 61   09 2018
    ## 62   09 2018
    ## 63   09 2018
    ## 64   09 2018
    ## 65   09 2018
    ## 66   09 2018
    ## 67   09 2018
    ## 68   09 2018
    ## 69   09 2018
    ## 70   09 2018
    ## 71   09 2018
    ## 72   09 2018
    ## 73   09 2018
    ## 74   09 2018
    ## 75   09 2018
    ## 76   09 2018
    ## 77   09 2018
    ## 78   09 2018
    ## 79   09 2018
    ## 80   09 2018
    ## 81   09 2018
    ## 82   09 2018
    ## 83   09 2018
    ## 84   09 2018
    ## 85   09 2018
    ## 86   09 2018
    ## 87   09 2018
    ## 88   09 2018
    ## 89   09 2018
    ## 90   09 2018
    ## 91   09 2018
    ## 92   09 2018
    ## 93   09 2018
    ## 94   09 2018
    ## 95   09 2018
    ## 96   09 2018
    ## 97   09 2018
    ## 98   09 2018
    ## 99   09 2018
    ## 100  09 2018
    ## 101  09 2018
    ## 102  09 2018
    ## 103  09 2018
    ## 104  09 2018
    ## 105  09 2018
    ## 106  09 2018
    ## 107  09 2018
    ## 108  09 2018
    ## 109  09 2018
    ## 110  09 2018
    ## 111  09 2018
    ## 112  09 2018
    ## 113  09 2018
    ## 114  09 2018
    ## 115  09 2018
    ## 116  09 2018
    ## 117  09 2018
    ## 118  09 2018
    ## 119  09 2018
    ## 120  09 2018
    ## 121  09 2018
    ## 122  09 2018
    ## 123  09 2018
    ## 124  09 2018
    ## 125  09 2018
    ## 126  09 2018
    ## 127  09 2018
    ## 128  09 2018
    ## 129  09 2018
    ## 130  09 2018
    ## 131  09 2018
    ## 132  09 2018
    ## 133  09 2018
    ## 134  09 2018
    ## 135  09 2018
    ## 136  09 2018
    ## 137  09 2018
    ## 138  09 2018
    ## 139  09 2018
    ## 140  09 2018
    ## 141  09 2018
    ## 142  09 2018
    ## 143  09 2018
    ## 144  09 2018
    ## 145  09 2018
    ## 146  09 2018
    ## 147  09 2018
    ## 148  09 2018
    ## 149  09 2018
    ## 150  09 2018
    ## 151  09 2018
    ## 152  09 2018
    ## 153  09 2018
    ## 154  09 2018
    ## 155  09 2018
    ## 156  09 2018
    ## 157  09 2018
    ## 158  09 2018
    ## 159  09 2018
    ## 160  09 2018
    ## 161  09 2018
    ## 162  09 2018
    ## 163  09 2018
    ## 164  09 2018
    ## 165  09 2018
    ## 166  09 2018
    ## 167  09 2018
    ## 168  09 2018
    ## 169  09 2018
    ## 170  09 2018
    ## 171  09 2018
    ## 172  09 2018
    ## 173  09 2018
    ## 174  09 2018
    ## 175  09 2018
    ## 176  09 2018
    ## 177  09 2018
    ## 178  09 2018
    ## 179  09 2018
    ## 180  09 2018
    ## 181  09 2018
    ## 182  09 2018
    ## 183  09 2018
    ## 184  09 2018
    ## 185  09 2018
    ## 186  09 2018
    ## 187  09 2018
    ## 188  09 2018
    ## 
    ## [[10]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10001784                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 2    10001785                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 3    10001786           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 4    10001787                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 5    10001788            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 6    10001789                            UBIQUO LABS |||FALTANTE     76001
    ## 7    10001790                          POLLO PINULITO|||FALTANTE     76002
    ## 8    10001791                                        UBIQUO LABS     76002
    ## 9    10001792                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 10   10001793                                TAQUERIA EL CHINITO     76001
    ## 11   10001794            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 12   10001795                              HOSPITAL LAS AMERICAS     76001
    ## 13   10001796                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 14   10001797           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 15   10001798                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 16   10001799 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 17   10001800        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 18   10001801            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 19   10001802                     EL PINCHE OBELISCO |||Faltante     76001
    ## 20   10001803                                TAQUERIA EL CHINITO     76001
    ## 21   10001804            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 22   10001805 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 23   10001806                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 24   10001807                            UBIQUO LABS |||FALTANTE     76001
    ## 25   10001808      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 26   10001809                            UBIQUO LABS |||FALTANTE     76002
    ## 27   10001810                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 28   10001811            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 29   10001812                              HOSPITAL LAS AMERICAS     76001
    ## 30   10001813                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 31   10001814            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 32   10001815           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 33   10001816            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 34   10001817                     EL PINCHE OBELISCO |||Faltante     76001
    ## 35   10001818                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 36   10001819                     EL PINCHE OBELISCO |||Faltante     76002
    ## 37   10001820                                     BAR LA OFICINA     76002
    ## 38   10001821            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 39   10001822        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 40   10001823                              HOSPITAL LAS AMERICAS     76002
    ## 41   10001824                                     BAR LA OFICINA     76001
    ## 42   10001825            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 43   10001826      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 44   10001827                              HOSPITAL LAS AMERICAS     76002
    ## 45   10001828                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 46   10001829                     EL PINCHE OBELISCO |||Faltante     76002
    ## 47   10001830            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 48   10001831        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 49   10001832                                     BAR LA OFICINA     76001
    ## 50   10001833                  POLLO PINULITO/Despacho a cliente     76002
    ## 51   10001834                  POLLO PINULITO/Despacho a cliente     76001
    ## 52   10001835        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 53   10001836            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 54   10001837                                        UBIQUO LABS     76001
    ## 55   10001838           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 56   10001839                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 57   10001840           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 58   10001841                EL GALLO NEGRO / Despacho a cliente     76002
    ## 59   10001842                                        UBIQUO LABS     76002
    ## 60   10001843                            UBIQUO LABS |||FALTANTE     76001
    ## 61   10001844                                TAQUERIA EL CHINITO     76002
    ## 62   10001845                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 63   10001846                            UBIQUO LABS |||FALTANTE     76001
    ## 64   10001847                                     BAR LA OFICINA     76001
    ## 65   10001848                                        UBIQUO LABS     76001
    ## 66   10001849                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 67   10001850                              HOSPITAL LAS AMERICAS     76001
    ## 68   10001851      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 69   10001852                            UBIQUO LABS |||FALTANTE     76001
    ## 70   10001853                                TAQUERIA EL CHINITO     76002
    ## 71   10001854           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 72   10001855            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 73   10001856                                     BAR LA OFICINA     76002
    ## 74   10001857           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 75   10001858                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 76   10001859                            UBIQUO LABS |||FALTANTE     76002
    ## 77   10001860                                        UBIQUO LABS     76001
    ## 78   10001861                EL GALLO NEGRO / Despacho a cliente     76002
    ## 79   10001862 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 80   10001863                            UBIQUO LABS |||FALTANTE     76001
    ## 81   10001864                     EL PINCHE OBELISCO |||Faltante     76002
    ## 82   10001865                          POLLO PINULITO|||FALTANTE     76001
    ## 83   10001866 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 84   10001867      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 85   10001868                                     BAR LA OFICINA     76002
    ## 86   10001869                                        UBIQUO LABS     76001
    ## 87   10001870 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 88   10001871            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 89   10001872 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 90   10001873            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 91   10001874                EL GALLO NEGRO / Despacho a cliente     76002
    ## 92   10001875      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 93   10001876           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 94   10001877                                TAQUERIA EL CHINITO     76001
    ## 95   10001878                EL GALLO NEGRO / Despacho a cliente     76002
    ## 96   10001879                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 97   10001880            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 98   10001881                            UBIQUO LABS |||FALTANTE     76001
    ## 99   10001882                                TAQUERIA EL CHINITO     76002
    ## 100  10001883                            UBIQUO LABS |||FALTANTE     76001
    ## 101  10001884            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 102  10001885                                     BAR LA OFICINA     76002
    ## 103  10001886                                     BAR LA OFICINA     76002
    ## 104  10001887                                     BAR LA OFICINA     76001
    ## 105  10001888                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 106  10001889                            UBIQUO LABS |||FALTANTE     76001
    ## 107  10001890                                TAQUERIA EL CHINITO     76001
    ## 108  10001891            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 109  10001892                     EL PINCHE OBELISCO |||Faltante     76001
    ## 110  10001893                            UBIQUO LABS |||FALTANTE     76001
    ## 111  10001894           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 112  10001895            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 113  10001896                          POLLO PINULITO|||FALTANTE     76002
    ## 114  10001897                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 115  10001898                                TAQUERIA EL CHINITO     76001
    ## 116  10001899                EL GALLO NEGRO / Despacho a cliente     76001
    ## 117  10001900 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 118  10001901                                TAQUERIA EL CHINITO     76002
    ## 119  10001902                                TAQUERIA EL CHINITO     76001
    ## 120  10001903                                TAQUERIA EL CHINITO     76001
    ## 121  10001904           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 122  10001905           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 123  10001906            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 124  10001907                              HOSPITAL LAS AMERICAS     76002
    ## 125  10001908                     EL PINCHE OBELISCO |||Faltante     76001
    ## 126  10001909      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 127  10001910            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 128  10001911                                        UBIQUO LABS     76002
    ## 129  10001912            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 130  10001913            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 131  10001914                                TAQUERIA EL CHINITO     76001
    ## 132  10001915      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 133  10001916                EL GALLO NEGRO / Despacho a cliente     76001
    ## 134  10001917            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 135  10001918                     EL PINCHE OBELISCO |||Faltante     76002
    ## 136  10001919        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 137  10001920        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 138  10001921 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 139  10001922                     EL PINCHE OBELISCO |||Faltante     76002
    ## 140  10001923      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 141  10001924           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 142  10001925                     EL PINCHE OBELISCO |||Faltante     76001
    ## 143  10001926                          POLLO PINULITO|||FALTANTE     76002
    ## 144  10001927            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 145  10001928                                        UBIQUO LABS     76001
    ## 146  10001929            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 147  10001930           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 148  10001931                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 149  10001932                                TAQUERIA EL CHINITO     76002
    ## 150  10001933                              HOSPITAL LAS AMERICAS     76001
    ## 151  10001934        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 152  10001935 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 153  10001936                  POLLO PINULITO/Despacho a cliente     76001
    ## 154  10001937           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 155  10001938                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 156  10001939            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 157  10001940                  POLLO PINULITO/Despacho a cliente     76001
    ## 158  10001941            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 159  10001942                  POLLO PINULITO/Despacho a cliente     76002
    ## 160  10001943                              HOSPITAL LAS AMERICAS     76001
    ## 161  10001944                          POLLO PINULITO|||FALTANTE     76002
    ## 162  10001945            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 163  10001946                                     BAR LA OFICINA     76002
    ## 164  10001947           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 165  10001948                                TAQUERIA EL CHINITO     76001
    ## 166  10001949                                TAQUERIA EL CHINITO     76002
    ## 167  10001950                                     BAR LA OFICINA     76002
    ## 168  10001951                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 169  10001952                                     BAR LA OFICINA     76001
    ## 170  10001953            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 171  10001954            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 172  10001955           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 173  10001956            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 174  10001957                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 175  10001958                                TAQUERIA EL CHINITO     76002
    ## 176  10001959           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 177  10001960            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 178  10001961                  POLLO PINULITO/Despacho a cliente     76001
    ## 179  10001962                              HOSPITAL LAS AMERICAS     76001
    ## 180  10001963           TIENDA LA BENDICION / Despacho a cliente     76002
    ## 181  10001964                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 182  10001965                                TAQUERIA EL CHINITO     76002
    ## 183  10001966        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 184  10001967                              HOSPITAL LAS AMERICAS     76002
    ## 185  10001968                                TAQUERIA EL CHINITO     76002
    ## 186  10001969                     EL PINCHE OBELISCO |||Faltante     76002
    ## 187  10001970                          POLLO PINULITO|||FALTANTE     76002
    ## 188  10001971      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 189  10001972      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 190  10001973                  POLLO PINULITO/Despacho a cliente     76002
    ## 191  10001974                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 192  10001975            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 193  10001976                EL GALLO NEGRO / Despacho a cliente     76001
    ## 194  10001977                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 195  10001978      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 196  10001979      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 197  10001980                EL GALLO NEGRO / Despacho a cliente     76001
    ## 198  10001981                     EL PINCHE OBELISCO |||Faltante     76002
    ## 199  10001982                            UBIQUO LABS |||FALTANTE     76002
    ## 200  10001983      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1        511      Ismael Rodero Monteagudo 127.75      30 Camion Pequeño
    ## 2        349             Luis Jaime Urbano  87.25      60          Panel
    ## 3       1278              Felipe Villatoro 319.50      60  Camion Grande
    ## 4        356          Angel Valdez Alegria  89.00      90          Panel
    ## 5       1427          Angel Valdez Alegria 356.75      30  Camion Grande
    ## 6       1949          Angel Valdez Alegria 487.25      90  Camion Grande
    ## 7       1586          Pedro Alvarez Parejo 396.50      60  Camion Grande
    ## 8       1368              Felipe Villatoro 342.00      60  Camion Grande
    ## 9        568                  Hector Giron 142.00      60 Camion Pequeño
    ## 10       864      Ismael Rodero Monteagudo 216.00      60 Camion Pequeño
    ## 11      1219          Angel Valdez Alegria 304.75      60  Camion Grande
    ## 12       425              Felipe Villatoro 106.25      90          Panel
    ## 13      1006        Hector Aragones Frutos 251.50      30  Camion Grande
    ## 14      1882      Ismael Rodero Monteagudo 470.50      60  Camion Grande
    ## 15       249 Juan Francisco Portillo Gomez  62.25      60          Panel
    ## 16      1323        Hector Aragones Frutos 330.75      90  Camion Grande
    ## 17      1236 Juan Francisco Portillo Gomez 309.00      30  Camion Grande
    ## 18      1161          Pedro Alvarez Parejo 290.25      90  Camion Grande
    ## 19      1453                  Hector Giron 363.25      60  Camion Grande
    ## 20       822              Felipe Villatoro 205.50      90 Camion Pequeño
    ## 21      1230       Fernando Mariano Berrio 307.50      30  Camion Grande
    ## 22       702          Pedro Alvarez Parejo 175.50      90 Camion Pequeño
    ## 23      1387          Angel Valdez Alegria 346.75      90  Camion Grande
    ## 24       412        Hector Aragones Frutos 103.00      60          Panel
    ## 25      1533      Ismael Rodero Monteagudo 383.25      30  Camion Grande
    ## 26      1945        Hector Aragones Frutos 486.25      90  Camion Grande
    ## 27       571 Juan Francisco Portillo Gomez 142.75      30 Camion Pequeño
    ## 28      1483              Felipe Villatoro 370.75      30  Camion Grande
    ## 29      1826                  Hector Giron 456.50      90  Camion Grande
    ## 30      1607          Pedro Alvarez Parejo 401.75      90  Camion Grande
    ## 31      1527       Fernando Mariano Berrio 381.75      30  Camion Grande
    ## 32      1282              Felipe Villatoro 320.50      30  Camion Grande
    ## 33       989          Pedro Alvarez Parejo 247.25      60 Camion Pequeño
    ## 34      1439                  Hector Giron 359.75      90  Camion Grande
    ## 35       532              Felipe Villatoro 133.00      30 Camion Pequeño
    ## 36       242             Luis Jaime Urbano  60.50      60          Panel
    ## 37      1950          Pedro Alvarez Parejo 487.50      90  Camion Grande
    ## 38      1149        Hector Aragones Frutos 287.25      60  Camion Grande
    ## 39      1813 Juan Francisco Portillo Gomez 453.25      90  Camion Grande
    ## 40       572              Felipe Villatoro 143.00      90 Camion Pequeño
    ## 41       820          Pedro Alvarez Parejo 205.00      30 Camion Pequeño
    ## 42      1105                  Hector Giron 276.25      60  Camion Grande
    ## 43      1604        Hector Aragones Frutos 401.00      90  Camion Grande
    ## 44       371             Luis Jaime Urbano  92.75      60          Panel
    ## 45      1365       Fernando Mariano Berrio 341.25      60  Camion Grande
    ## 46      1796       Fernando Mariano Berrio 449.00      30  Camion Grande
    ## 47      1443                  Hector Giron 360.75      60  Camion Grande
    ## 48      1728          Angel Valdez Alegria 432.00      30  Camion Grande
    ## 49       884       Fernando Mariano Berrio 221.00      60 Camion Pequeño
    ## 50      1135          Angel Valdez Alegria 283.75      30  Camion Grande
    ## 51       714          Angel Valdez Alegria 178.50      30 Camion Pequeño
    ## 52      1342        Hector Aragones Frutos 335.50      30  Camion Grande
    ## 53       549      Ismael Rodero Monteagudo 137.25      30 Camion Pequeño
    ## 54      1303              Felipe Villatoro 325.75      30  Camion Grande
    ## 55      1437          Pedro Alvarez Parejo 359.25      60  Camion Grande
    ## 56       257      Ismael Rodero Monteagudo  64.25      60          Panel
    ## 57       429       Fernando Mariano Berrio 107.25      60          Panel
    ## 58      1231          Pedro Alvarez Parejo 307.75      60  Camion Grande
    ## 59      1434          Pedro Alvarez Parejo 358.50      60  Camion Grande
    ## 60      1000              Felipe Villatoro 250.00      90 Camion Pequeño
    ## 61      1148      Ismael Rodero Monteagudo 287.00      90  Camion Grande
    ## 62      1347        Hector Aragones Frutos 336.75      60  Camion Grande
    ## 63       802        Hector Aragones Frutos 200.50      30 Camion Pequeño
    ## 64      1919        Hector Aragones Frutos 479.75      30  Camion Grande
    ## 65       717 Juan Francisco Portillo Gomez 179.25      60 Camion Pequeño
    ## 66       838       Fernando Mariano Berrio 209.50      90 Camion Pequeño
    ## 67       324       Fernando Mariano Berrio  81.00      90          Panel
    ## 68      1309      Ismael Rodero Monteagudo 327.25      60  Camion Grande
    ## 69      1333                  Hector Giron 333.25      30  Camion Grande
    ## 70      1496             Luis Jaime Urbano 374.00      90  Camion Grande
    ## 71       327              Felipe Villatoro  81.75      30          Panel
    ## 72      1662        Hector Aragones Frutos 415.50      30  Camion Grande
    ## 73      1479      Ismael Rodero Monteagudo 369.75      30  Camion Grande
    ## 74       939      Ismael Rodero Monteagudo 234.75      60 Camion Pequeño
    ## 75       429              Felipe Villatoro 107.25      30          Panel
    ## 76      1734                  Hector Giron 433.50      90  Camion Grande
    ## 77       667 Juan Francisco Portillo Gomez 166.75      90 Camion Pequeño
    ## 78      1054       Fernando Mariano Berrio 263.50      60  Camion Grande
    ## 79       913              Felipe Villatoro 228.25      30 Camion Pequeño
    ## 80      1583        Hector Aragones Frutos 395.75      90  Camion Grande
    ## 81      1067                  Hector Giron 266.75      90  Camion Grande
    ## 82      1206       Fernando Mariano Berrio 301.50      30  Camion Grande
    ## 83      1366          Angel Valdez Alegria 341.50      30  Camion Grande
    ## 84      1651       Fernando Mariano Berrio 412.75      90  Camion Grande
    ## 85       481              Felipe Villatoro 120.25      90          Panel
    ## 86       975      Ismael Rodero Monteagudo 243.75      30 Camion Pequeño
    ## 87       981              Felipe Villatoro 245.25      90 Camion Pequeño
    ## 88       558                  Hector Giron 139.50      30 Camion Pequeño
    ## 89       476          Pedro Alvarez Parejo 119.00      30          Panel
    ## 90       791       Fernando Mariano Berrio 197.75      60 Camion Pequeño
    ## 91       353          Angel Valdez Alegria  88.25      60          Panel
    ## 92      1812          Angel Valdez Alegria 453.00      30  Camion Grande
    ## 93       884              Felipe Villatoro 221.00      60 Camion Pequeño
    ## 94      1055             Luis Jaime Urbano 263.75      30  Camion Grande
    ## 95       831             Luis Jaime Urbano 207.75      60 Camion Pequeño
    ## 96       623             Luis Jaime Urbano 155.75      60 Camion Pequeño
    ## 97       488        Hector Aragones Frutos 122.00      30          Panel
    ## 98       980          Angel Valdez Alegria 245.00      90 Camion Pequeño
    ## 99      1772                  Hector Giron 443.00      30  Camion Grande
    ## 100     1164       Fernando Mariano Berrio 291.00      60  Camion Grande
    ## 101      695          Angel Valdez Alegria 173.75      90 Camion Pequeño
    ## 102      904          Pedro Alvarez Parejo 226.00      30 Camion Pequeño
    ## 103     1022          Angel Valdez Alegria 255.50      90  Camion Grande
    ## 104      671             Luis Jaime Urbano 167.75      60 Camion Pequeño
    ## 105      523          Pedro Alvarez Parejo 130.75      60 Camion Pequeño
    ## 106      988             Luis Jaime Urbano 247.00      90 Camion Pequeño
    ## 107      550 Juan Francisco Portillo Gomez 137.50      30 Camion Pequeño
    ## 108     1314 Juan Francisco Portillo Gomez 328.50      60  Camion Grande
    ## 109      956 Juan Francisco Portillo Gomez 239.00      60 Camion Pequeño
    ## 110     1432       Fernando Mariano Berrio 358.00      90  Camion Grande
    ## 111      805          Pedro Alvarez Parejo 201.25      60 Camion Pequeño
    ## 112     1710      Ismael Rodero Monteagudo 427.50      60  Camion Grande
    ## 113     1496 Juan Francisco Portillo Gomez 374.00      60  Camion Grande
    ## 114     1771              Felipe Villatoro 442.75      60  Camion Grande
    ## 115     1416 Juan Francisco Portillo Gomez 354.00      30  Camion Grande
    ## 116      237              Felipe Villatoro  59.25      60          Panel
    ## 117     1771          Angel Valdez Alegria 442.75      60  Camion Grande
    ## 118      625       Fernando Mariano Berrio 156.25      30 Camion Pequeño
    ## 119      254          Pedro Alvarez Parejo  63.50      30          Panel
    ## 120      789      Ismael Rodero Monteagudo 197.25      30 Camion Pequeño
    ## 121     1191        Hector Aragones Frutos 297.75      90  Camion Grande
    ## 122     1947        Hector Aragones Frutos 486.75      60  Camion Grande
    ## 123     1121                  Hector Giron 280.25      30  Camion Grande
    ## 124     1960      Ismael Rodero Monteagudo 490.00      60  Camion Grande
    ## 125     1272          Pedro Alvarez Parejo 318.00      90  Camion Grande
    ## 126      889                  Hector Giron 222.25      60 Camion Pequeño
    ## 127      709          Pedro Alvarez Parejo 177.25      60 Camion Pequeño
    ## 128      981              Felipe Villatoro 245.25      90 Camion Pequeño
    ## 129      840      Ismael Rodero Monteagudo 210.00      90 Camion Pequeño
    ## 130     1145              Felipe Villatoro 286.25      60  Camion Grande
    ## 131      893                  Hector Giron 223.25      30 Camion Pequeño
    ## 132     1674          Pedro Alvarez Parejo 418.50      30  Camion Grande
    ## 133     1110       Fernando Mariano Berrio 277.50      90  Camion Grande
    ## 134     1341       Fernando Mariano Berrio 335.25      60  Camion Grande
    ## 135      999             Luis Jaime Urbano 249.75      60 Camion Pequeño
    ## 136      628      Ismael Rodero Monteagudo 157.00      90 Camion Pequeño
    ## 137      356             Luis Jaime Urbano  89.00      90          Panel
    ## 138     1596              Felipe Villatoro 399.00      30  Camion Grande
    ## 139     1855      Ismael Rodero Monteagudo 463.75      60  Camion Grande
    ## 140     1262          Pedro Alvarez Parejo 315.50      90  Camion Grande
    ## 141      620      Ismael Rodero Monteagudo 155.00      60 Camion Pequeño
    ## 142      647          Angel Valdez Alegria 161.75      30 Camion Pequeño
    ## 143      417          Pedro Alvarez Parejo 104.25      60          Panel
    ## 144     1865             Luis Jaime Urbano 466.25      90  Camion Grande
    ## 145      889       Fernando Mariano Berrio 222.25      90 Camion Pequeño
    ## 146      821             Luis Jaime Urbano 205.25      90 Camion Pequeño
    ## 147      918 Juan Francisco Portillo Gomez 229.50      90 Camion Pequeño
    ## 148     1399                  Hector Giron 349.75      60  Camion Grande
    ## 149      597             Luis Jaime Urbano 149.25      60 Camion Pequeño
    ## 150      638      Ismael Rodero Monteagudo 159.50      30 Camion Pequeño
    ## 151     1921      Ismael Rodero Monteagudo 480.25      60  Camion Grande
    ## 152      284 Juan Francisco Portillo Gomez  71.00      90          Panel
    ## 153      387          Pedro Alvarez Parejo  96.75      60          Panel
    ## 154      374                  Hector Giron  93.50      30          Panel
    ## 155     1878          Pedro Alvarez Parejo 469.50      30  Camion Grande
    ## 156     1969        Hector Aragones Frutos 492.25      60  Camion Grande
    ## 157     1199             Luis Jaime Urbano 299.75      60  Camion Grande
    ## 158     1480          Pedro Alvarez Parejo 370.00      90  Camion Grande
    ## 159     1809          Angel Valdez Alegria 452.25      60  Camion Grande
    ## 160     1058             Luis Jaime Urbano 264.50      60  Camion Grande
    ## 161      708             Luis Jaime Urbano 177.00      90 Camion Pequeño
    ## 162      355          Pedro Alvarez Parejo  88.75      60          Panel
    ## 163      374       Fernando Mariano Berrio  93.50      90          Panel
    ## 164     1641                  Hector Giron 410.25      90  Camion Grande
    ## 165     1771        Hector Aragones Frutos 442.75      30  Camion Grande
    ## 166     1166 Juan Francisco Portillo Gomez 291.50      60  Camion Grande
    ## 167      691       Fernando Mariano Berrio 172.75      60 Camion Pequeño
    ## 168     1658        Hector Aragones Frutos 414.50      30  Camion Grande
    ## 169      670          Pedro Alvarez Parejo 167.50      30 Camion Pequeño
    ## 170      832                  Hector Giron 208.00      90 Camion Pequeño
    ## 171      205             Luis Jaime Urbano  51.25      60          Panel
    ## 172     1562          Pedro Alvarez Parejo 390.50      90  Camion Grande
    ## 173      980          Pedro Alvarez Parejo 245.00      60 Camion Pequeño
    ## 174     1297          Angel Valdez Alegria 324.25      90  Camion Grande
    ## 175     1817      Ismael Rodero Monteagudo 454.25      30  Camion Grande
    ## 176      676 Juan Francisco Portillo Gomez 169.00      90 Camion Pequeño
    ## 177     1880             Luis Jaime Urbano 470.00      30  Camion Grande
    ## 178      578       Fernando Mariano Berrio 144.50      60 Camion Pequeño
    ## 179     1762          Angel Valdez Alegria 440.50      30  Camion Grande
    ## 180     1737              Felipe Villatoro 434.25      60  Camion Grande
    ## 181     1819              Felipe Villatoro 454.75      30  Camion Grande
    ## 182      508              Felipe Villatoro 127.00      90 Camion Pequeño
    ## 183      446      Ismael Rodero Monteagudo 111.50      90          Panel
    ## 184      597        Hector Aragones Frutos 149.25      30 Camion Pequeño
    ## 185     1771      Ismael Rodero Monteagudo 442.75      90  Camion Grande
    ## 186     1808       Fernando Mariano Berrio 452.00      30  Camion Grande
    ## 187     1720              Felipe Villatoro 430.00      30  Camion Grande
    ## 188     1483      Ismael Rodero Monteagudo 370.75      30  Camion Grande
    ## 189     1155          Pedro Alvarez Parejo 288.75      90  Camion Grande
    ## 190     1011 Juan Francisco Portillo Gomez 252.75      90  Camion Grande
    ## 191     1228             Luis Jaime Urbano 307.00      30  Camion Grande
    ## 192     1751 Juan Francisco Portillo Gomez 437.75      90  Camion Grande
    ## 193     1874                  Hector Giron 468.50      30  Camion Grande
    ## 194     1679       Fernando Mariano Berrio 419.75      60  Camion Grande
    ## 195      945              Felipe Villatoro 236.25      90 Camion Pequeño
    ## 196     1605              Felipe Villatoro 401.25      60  Camion Grande
    ## 197     1931       Fernando Mariano Berrio 482.75      30  Camion Grande
    ## 198      225        Hector Aragones Frutos  56.25      60          Panel
    ## 199      263       Fernando Mariano Berrio  65.75      30          Panel
    ## 200      967      Ismael Rodero Monteagudo 241.75      90 Camion Pequeño
    ##     mes anio
    ## 1    10 2018
    ## 2    10 2018
    ## 3    10 2018
    ## 4    10 2018
    ## 5    10 2018
    ## 6    10 2018
    ## 7    10 2018
    ## 8    10 2018
    ## 9    10 2018
    ## 10   10 2018
    ## 11   10 2018
    ## 12   10 2018
    ## 13   10 2018
    ## 14   10 2018
    ## 15   10 2018
    ## 16   10 2018
    ## 17   10 2018
    ## 18   10 2018
    ## 19   10 2018
    ## 20   10 2018
    ## 21   10 2018
    ## 22   10 2018
    ## 23   10 2018
    ## 24   10 2018
    ## 25   10 2018
    ## 26   10 2018
    ## 27   10 2018
    ## 28   10 2018
    ## 29   10 2018
    ## 30   10 2018
    ## 31   10 2018
    ## 32   10 2018
    ## 33   10 2018
    ## 34   10 2018
    ## 35   10 2018
    ## 36   10 2018
    ## 37   10 2018
    ## 38   10 2018
    ## 39   10 2018
    ## 40   10 2018
    ## 41   10 2018
    ## 42   10 2018
    ## 43   10 2018
    ## 44   10 2018
    ## 45   10 2018
    ## 46   10 2018
    ## 47   10 2018
    ## 48   10 2018
    ## 49   10 2018
    ## 50   10 2018
    ## 51   10 2018
    ## 52   10 2018
    ## 53   10 2018
    ## 54   10 2018
    ## 55   10 2018
    ## 56   10 2018
    ## 57   10 2018
    ## 58   10 2018
    ## 59   10 2018
    ## 60   10 2018
    ## 61   10 2018
    ## 62   10 2018
    ## 63   10 2018
    ## 64   10 2018
    ## 65   10 2018
    ## 66   10 2018
    ## 67   10 2018
    ## 68   10 2018
    ## 69   10 2018
    ## 70   10 2018
    ## 71   10 2018
    ## 72   10 2018
    ## 73   10 2018
    ## 74   10 2018
    ## 75   10 2018
    ## 76   10 2018
    ## 77   10 2018
    ## 78   10 2018
    ## 79   10 2018
    ## 80   10 2018
    ## 81   10 2018
    ## 82   10 2018
    ## 83   10 2018
    ## 84   10 2018
    ## 85   10 2018
    ## 86   10 2018
    ## 87   10 2018
    ## 88   10 2018
    ## 89   10 2018
    ## 90   10 2018
    ## 91   10 2018
    ## 92   10 2018
    ## 93   10 2018
    ## 94   10 2018
    ## 95   10 2018
    ## 96   10 2018
    ## 97   10 2018
    ## 98   10 2018
    ## 99   10 2018
    ## 100  10 2018
    ## 101  10 2018
    ## 102  10 2018
    ## 103  10 2018
    ## 104  10 2018
    ## 105  10 2018
    ## 106  10 2018
    ## 107  10 2018
    ## 108  10 2018
    ## 109  10 2018
    ## 110  10 2018
    ## 111  10 2018
    ## 112  10 2018
    ## 113  10 2018
    ## 114  10 2018
    ## 115  10 2018
    ## 116  10 2018
    ## 117  10 2018
    ## 118  10 2018
    ## 119  10 2018
    ## 120  10 2018
    ## 121  10 2018
    ## 122  10 2018
    ## 123  10 2018
    ## 124  10 2018
    ## 125  10 2018
    ## 126  10 2018
    ## 127  10 2018
    ## 128  10 2018
    ## 129  10 2018
    ## 130  10 2018
    ## 131  10 2018
    ## 132  10 2018
    ## 133  10 2018
    ## 134  10 2018
    ## 135  10 2018
    ## 136  10 2018
    ## 137  10 2018
    ## 138  10 2018
    ## 139  10 2018
    ## 140  10 2018
    ## 141  10 2018
    ## 142  10 2018
    ## 143  10 2018
    ## 144  10 2018
    ## 145  10 2018
    ## 146  10 2018
    ## 147  10 2018
    ## 148  10 2018
    ## 149  10 2018
    ## 150  10 2018
    ## 151  10 2018
    ## 152  10 2018
    ## 153  10 2018
    ## 154  10 2018
    ## 155  10 2018
    ## 156  10 2018
    ## 157  10 2018
    ## 158  10 2018
    ## 159  10 2018
    ## 160  10 2018
    ## 161  10 2018
    ## 162  10 2018
    ## 163  10 2018
    ## 164  10 2018
    ## 165  10 2018
    ## 166  10 2018
    ## 167  10 2018
    ## 168  10 2018
    ## 169  10 2018
    ## 170  10 2018
    ## 171  10 2018
    ## 172  10 2018
    ## 173  10 2018
    ## 174  10 2018
    ## 175  10 2018
    ## 176  10 2018
    ## 177  10 2018
    ## 178  10 2018
    ## 179  10 2018
    ## 180  10 2018
    ## 181  10 2018
    ## 182  10 2018
    ## 183  10 2018
    ## 184  10 2018
    ## 185  10 2018
    ## 186  10 2018
    ## 187  10 2018
    ## 188  10 2018
    ## 189  10 2018
    ## 190  10 2018
    ## 191  10 2018
    ## 192  10 2018
    ## 193  10 2018
    ## 194  10 2018
    ## 195  10 2018
    ## 196  10 2018
    ## 197  10 2018
    ## 198  10 2018
    ## 199  10 2018
    ## 200  10 2018
    ## 
    ## [[11]]
    ##     COD_VIAJE                                            CLIENTE UBICACION
    ## 1    10001984                EL GALLO NEGRO / Despacho a cliente     76001
    ## 2    10001985            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 3    10001986                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 4    10001987                                        UBIQUO LABS     76001
    ## 5    10001988      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 6    10001989                              HOSPITAL LAS AMERICAS     76001
    ## 7    10001990                            UBIQUO LABS |||FALTANTE     76001
    ## 8    10001991                                TAQUERIA EL CHINITO     76002
    ## 9    10001992                                     BAR LA OFICINA     76002
    ## 10   10001993        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 11   10001994                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 12   10001995      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 13   10001996                                     BAR LA OFICINA     76002
    ## 14   10001997            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 15   10001998                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 16   10001999                                     BAR LA OFICINA     76001
    ## 17   10002000                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 18   10002001 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 19   10002002                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 20   10002003                                TAQUERIA EL CHINITO     76001
    ## 21   10002004                EL GALLO NEGRO / Despacho a cliente     76001
    ## 22   10002005            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 23   10002006        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 24   10002007 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 25   10002008            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 26   10002009        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 27   10002010           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 28   10002011                                     BAR LA OFICINA     76001
    ## 29   10002012                                TAQUERIA EL CHINITO     76001
    ## 30   10002013                                        UBIQUO LABS     76002
    ## 31   10002014                     EL PINCHE OBELISCO |||Faltante     76002
    ## 32   10002015                          POLLO PINULITO|||FALTANTE     76002
    ## 33   10002016      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 34   10002017                                        UBIQUO LABS     76002
    ## 35   10002018            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 36   10002019                            UBIQUO LABS |||FALTANTE     76002
    ## 37   10002020                EL GALLO NEGRO / Despacho a cliente     76002
    ## 38   10002021           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 39   10002022 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 40   10002023            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 41   10002024                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 42   10002025                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 43   10002026            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 44   10002027                     EL PINCHE OBELISCO |||Faltante     76001
    ## 45   10002028                          POLLO PINULITO|||FALTANTE     76001
    ## 46   10002029                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 47   10002030                EL GALLO NEGRO / Despacho a cliente     76002
    ## 48   10002031                              HOSPITAL LAS AMERICAS     76001
    ## 49   10002032            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 50   10002033                                TAQUERIA EL CHINITO     76002
    ## 51   10002034                     EL PINCHE OBELISCO |||Faltante     76001
    ## 52   10002035                              HOSPITAL LAS AMERICAS     76002
    ## 53   10002036                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 54   10002037                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 55   10002038                          POLLO PINULITO|||FALTANTE     76001
    ## 56   10002039            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 57   10002040                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 58   10002041                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 59   10002042                EL GALLO NEGRO / Despacho a cliente     76001
    ## 60   10002043                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 61   10002044                EL GALLO NEGRO / Despacho a cliente     76002
    ## 62   10002045                          POLLO PINULITO|||FALTANTE     76002
    ## 63   10002046                                        UBIQUO LABS     76002
    ## 64   10002047                                TAQUERIA EL CHINITO     76002
    ## 65   10002048           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 66   10002049                              HOSPITAL LAS AMERICAS     76002
    ## 67   10002050                                        UBIQUO LABS     76001
    ## 68   10002051                EL GALLO NEGRO / Despacho a cliente     76002
    ## 69   10002052           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 70   10002053           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 71   10002054                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 72   10002055                              HOSPITAL LAS AMERICAS     76001
    ## 73   10002056        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 74   10002057                                     BAR LA OFICINA     76002
    ## 75   10002058                                TAQUERIA EL CHINITO     76002
    ## 76   10002059           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 77   10002060                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 78   10002061                          POLLO PINULITO|||FALTANTE     76002
    ## 79   10002062                                TAQUERIA EL CHINITO     76002
    ## 80   10002063                                     BAR LA OFICINA     76001
    ## 81   10002064                     EL PINCHE OBELISCO |||Faltante     76002
    ## 82   10002065                       EL GALLO NEGRO |||DEVOLUCION     76002
    ## 83   10002066                     EL PINCHE OBELISCO |||Faltante     76002
    ## 84   10002067                          POLLO PINULITO|||FALTANTE     76002
    ## 85   10002068 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 86   10002069            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 87   10002070 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 88   10002071 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76002
    ## 89   10002072                              HOSPITAL LAS AMERICAS     76001
    ## 90   10002073           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 91   10002074                          POLLO PINULITO|||FALTANTE     76001
    ## 92   10002075            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 93   10002076                          POLLO PINULITO|||FALTANTE     76001
    ## 94   10002077                EL GALLO NEGRO / Despacho a cliente     76002
    ## 95   10002078        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 96   10002079                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 97   10002080                  POLLO PINULITO/Despacho a cliente     76002
    ## 98   10002081                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 99   10002082                              HOSPITAL LAS AMERICAS     76001
    ## 100  10002083                            UBIQUO LABS |||FALTANTE     76002
    ## 101  10002084      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 102  10002085            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 103  10002086           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 104  10002087                          POLLO PINULITO|||FALTANTE     76001
    ## 105  10002088                          POLLO PINULITO|||FALTANTE     76001
    ## 106  10002089                  POLLO PINULITO/Despacho a cliente     76001
    ## 107  10002090           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 108  10002091                     EL PINCHE OBELISCO |||Faltante     76001
    ## 109  10002092                              HOSPITAL LAS AMERICAS     76002
    ## 110  10002093      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 111  10002094           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 112  10002095                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 113  10002096                                TAQUERIA EL CHINITO     76002
    ## 114  10002097                  POLLO PINULITO/Despacho a cliente     76001
    ## 115  10002098                EL GALLO NEGRO / Despacho a cliente     76001
    ## 116  10002099                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 117  10002100                              HOSPITAL LAS AMERICAS     76001
    ## 118  10002101                                     BAR LA OFICINA     76002
    ## 119  10002102                                     BAR LA OFICINA     76001
    ## 120  10002103                     EL PINCHE OBELISCO |||Faltante     76002
    ## 121  10002104            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 122  10002105                              HOSPITAL LAS AMERICAS     76001
    ## 123  10002106                  POLLO PINULITO/Despacho a cliente     76002
    ## 124  10002107           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 125  10002108           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 126  10002109                              HOSPITAL LAS AMERICAS     76002
    ## 127  10002110                                TAQUERIA EL CHINITO     76002
    ## 128  10002111                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 129  10002112            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 130  10002113                                     BAR LA OFICINA     76001
    ## 131  10002114            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 132  10002115                                     BAR LA OFICINA     76001
    ## 133  10002116           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 134  10002117                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 135  10002118                                     BAR LA OFICINA     76002
    ## 136  10002119                          POLLO PINULITO|||FALTANTE     76002
    ## 137  10002120            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 138  10002121      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 139  10002122        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 140  10002123           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 141  10002124                EL GALLO NEGRO / Despacho a cliente     76002
    ## 142  10002125            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 143  10002126            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 144  10002127        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 145  10002128                              HOSPITAL LAS AMERICAS     76001
    ## 146  10002129                                TAQUERIA EL CHINITO     76002
    ## 147  10002130                          POLLO PINULITO|||FALTANTE     76001
    ## 148  10002131                     EL PINCHE OBELISCO |||Faltante     76002
    ## 149  10002132                            UBIQUO LABS |||FALTANTE     76002
    ## 150  10002133                EL GALLO NEGRO / Despacho a cliente     76001
    ## 151  10002134        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 152  10002135                          POLLO PINULITO|||FALTANTE     76002
    ## 153  10002136                EL GALLO NEGRO / Despacho a cliente     76002
    ## 154  10002137      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 155  10002138            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 156  10002139           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 157  10002140                                TAQUERIA EL CHINITO     76002
    ## 158  10002141        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 159  10002142            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ## 160  10002143 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 161  10002144            EL PINCHE OBELISCO / Despacho a cliente     76002
    ## 162  10002145           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 163  10002146                EL GALLO NEGRO / Despacho a cliente     76002
    ## 164  10002147                                     BAR LA OFICINA     76002
    ## 165  10002148                       EL GALLO NEGRO |||DEVOLUCION     76001
    ## 166  10002149        SPORTA, S.A./Despacho a cliente |||Faltante     76002
    ## 167  10002150           TIENDA LA BENDICION / Despacho a cliente     76001
    ## 168  10002151                                        UBIQUO LABS     76001
    ## 169  10002152                          POLLO PINULITO|||FALTANTE     76001
    ## 170  10002153                                     BAR LA OFICINA     76001
    ## 171  10002154           HOSPITAL ROOSEVELT / Despacho a cliente      76002
    ## 172  10002155           HOSPITAL ROOSEVELT / Despacho a cliente      76001
    ## 173  10002156                     EL PINCHE OBELISCO |||Faltante     76002
    ## 174  10002157                          POLLO PINULITO|||FALTANTE     76002
    ## 175  10002158                     EL PINCHE OBELISCO |||Faltante     76002
    ## 176  10002159                     EL PINCHE OBELISCO |||Faltante     76001
    ## 177  10002160            ABARROTERIA EBENEZER/Despacho a cliente     76002
    ## 178  10002161      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 179  10002162      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76002
    ## 180  10002163                              HOSPITAL LAS AMERICAS     76002
    ## 181  10002164                              HOSPITAL LAS AMERICAS     76002
    ## 182  10002165                                     BAR LA OFICINA     76002
    ## 183  10002166 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente     76001
    ## 184  10002167                EL GALLO NEGRO / Despacho a cliente     76001
    ## 185  10002168            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 186  10002169                    TAQUERIA EL CHINITO |||Faltante     76002
    ## 187  10002170      CHICHARRONERIA EL RICO COLESTEROL |||Faltante     76001
    ## 188  10002171                                        UBIQUO LABS     76002
    ## 189  10002172                                     BAR LA OFICINA     76002
    ## 190  10002173                  POLLO PINULITO/Despacho a cliente     76002
    ## 191  10002174        SPORTA, S.A./Despacho a cliente |||Faltante     76001
    ## 192  10002175                    TAQUERIA EL CHINITO |||Faltante     76001
    ## 193  10002176                                     BAR LA OFICINA     76002
    ## 194  10002177            EL PINCHE OBELISCO / Despacho a cliente     76001
    ## 195  10002178                            UBIQUO LABS |||FALTANTE     76002
    ## 196  10002179                EL GALLO NEGRO / Despacho a cliente     76001
    ## 197  10002180            ABARROTERIA EBENEZER/Despacho a cliente     76001
    ##     CANTIDAD                        PILOTO      Q CREDITO         UNIDAD
    ## 1       1639      Ismael Rodero Monteagudo 409.75      30  Camion Grande
    ## 2       1811          Angel Valdez Alegria 452.75      60  Camion Grande
    ## 3        676 Juan Francisco Portillo Gomez 169.00      60 Camion Pequeño
    ## 4        566        Hector Aragones Frutos 141.50      90 Camion Pequeño
    ## 5       1723      Ismael Rodero Monteagudo 430.75      30  Camion Grande
    ## 6        873          Pedro Alvarez Parejo 218.25      90 Camion Pequeño
    ## 7       1524          Pedro Alvarez Parejo 381.00      30  Camion Grande
    ## 8        805          Pedro Alvarez Parejo 201.25      90 Camion Pequeño
    ## 9       1382       Fernando Mariano Berrio 345.50      30  Camion Grande
    ## 10      1430          Pedro Alvarez Parejo 357.50      60  Camion Grande
    ## 11      1055              Felipe Villatoro 263.75      90  Camion Grande
    ## 12      1862          Pedro Alvarez Parejo 465.50      60  Camion Grande
    ## 13      1881       Fernando Mariano Berrio 470.25      30  Camion Grande
    ## 14      1025          Angel Valdez Alegria 256.25      90  Camion Grande
    ## 15       836              Felipe Villatoro 209.00      90 Camion Pequeño
    ## 16       205          Pedro Alvarez Parejo  51.25      60          Panel
    ## 17      1876 Juan Francisco Portillo Gomez 469.00      30  Camion Grande
    ## 18      1065              Felipe Villatoro 266.25      60  Camion Grande
    ## 19      1597          Pedro Alvarez Parejo 399.25      60  Camion Grande
    ## 20      1606             Luis Jaime Urbano 401.50      90  Camion Grande
    ## 21      1986        Hector Aragones Frutos 496.50      60  Camion Grande
    ## 22      1233      Ismael Rodero Monteagudo 308.25      90  Camion Grande
    ## 23      1757       Fernando Mariano Berrio 439.25      90  Camion Grande
    ## 24       477 Juan Francisco Portillo Gomez 119.25      60          Panel
    ## 25       531          Pedro Alvarez Parejo 132.75      30 Camion Pequeño
    ## 26       826              Felipe Villatoro 206.50      30 Camion Pequeño
    ## 27      1075        Hector Aragones Frutos 268.75      30  Camion Grande
    ## 28      1556          Angel Valdez Alegria 389.00      90  Camion Grande
    ## 29      1850 Juan Francisco Portillo Gomez 462.50      60  Camion Grande
    ## 30       359          Pedro Alvarez Parejo  89.75      60          Panel
    ## 31      1173          Angel Valdez Alegria 293.25      30  Camion Grande
    ## 32      1883             Luis Jaime Urbano 470.75      90  Camion Grande
    ## 33       289      Ismael Rodero Monteagudo  72.25      60          Panel
    ## 34      1087 Juan Francisco Portillo Gomez 271.75      90  Camion Grande
    ## 35       946       Fernando Mariano Berrio 236.50      30 Camion Pequeño
    ## 36      1950          Pedro Alvarez Parejo 487.50      60  Camion Grande
    ## 37       938       Fernando Mariano Berrio 234.50      60 Camion Pequeño
    ## 38      1092      Ismael Rodero Monteagudo 273.00      60  Camion Grande
    ## 39      1256             Luis Jaime Urbano 314.00      90  Camion Grande
    ## 40       959        Hector Aragones Frutos 239.75      60 Camion Pequeño
    ## 41      1699          Angel Valdez Alegria 424.75      60  Camion Grande
    ## 42       612          Pedro Alvarez Parejo 153.00      30 Camion Pequeño
    ## 43      1991              Felipe Villatoro 497.75      30  Camion Grande
    ## 44      1105          Angel Valdez Alegria 276.25      30  Camion Grande
    ## 45      1973      Ismael Rodero Monteagudo 493.25      60  Camion Grande
    ## 46       768             Luis Jaime Urbano 192.00      30 Camion Pequeño
    ## 47      1364       Fernando Mariano Berrio 341.00      90  Camion Grande
    ## 48       838             Luis Jaime Urbano 209.50      60 Camion Pequeño
    ## 49       641        Hector Aragones Frutos 160.25      90 Camion Pequeño
    ## 50      1842          Angel Valdez Alegria 460.50      60  Camion Grande
    ## 51       505                  Hector Giron 126.25      60 Camion Pequeño
    ## 52      1817          Pedro Alvarez Parejo 454.25      90  Camion Grande
    ## 53       890          Angel Valdez Alegria 222.50      30 Camion Pequeño
    ## 54       466          Pedro Alvarez Parejo 116.50      30          Panel
    ## 55       410          Pedro Alvarez Parejo 102.50      60          Panel
    ## 56       599        Hector Aragones Frutos 149.75      30 Camion Pequeño
    ## 57      1771      Ismael Rodero Monteagudo 442.75      60  Camion Grande
    ## 58       632 Juan Francisco Portillo Gomez 158.00      60 Camion Pequeño
    ## 59      1935      Ismael Rodero Monteagudo 483.75      60  Camion Grande
    ## 60      1761       Fernando Mariano Berrio 440.25      60  Camion Grande
    ## 61       952              Felipe Villatoro 238.00      90 Camion Pequeño
    ## 62       640      Ismael Rodero Monteagudo 160.00      90 Camion Pequeño
    ## 63      1103       Fernando Mariano Berrio 275.75      90  Camion Grande
    ## 64      1577       Fernando Mariano Berrio 394.25      90  Camion Grande
    ## 65      1778             Luis Jaime Urbano 444.50      30  Camion Grande
    ## 66      1595       Fernando Mariano Berrio 398.75      60  Camion Grande
    ## 67      1857              Felipe Villatoro 464.25      60  Camion Grande
    ## 68       554                  Hector Giron 138.50      90 Camion Pequeño
    ## 69      1501                  Hector Giron 375.25      90  Camion Grande
    ## 70       966 Juan Francisco Portillo Gomez 241.50      90 Camion Pequeño
    ## 71      1813             Luis Jaime Urbano 453.25      90  Camion Grande
    ## 72      1419              Felipe Villatoro 354.75      30  Camion Grande
    ## 73      1512              Felipe Villatoro 378.00      60  Camion Grande
    ## 74       295        Hector Aragones Frutos  73.75      30          Panel
    ## 75      1775                  Hector Giron 443.75      90  Camion Grande
    ## 76       334          Pedro Alvarez Parejo  83.50      30          Panel
    ## 77      1184          Angel Valdez Alegria 296.00      60  Camion Grande
    ## 78      1873        Hector Aragones Frutos 468.25      30  Camion Grande
    ## 79      1096          Pedro Alvarez Parejo 274.00      60  Camion Grande
    ## 80      1387                  Hector Giron 346.75      90  Camion Grande
    ## 81      1043             Luis Jaime Urbano 260.75      90  Camion Grande
    ## 82       691        Hector Aragones Frutos 172.75      60 Camion Pequeño
    ## 83      1731       Fernando Mariano Berrio 432.75      60  Camion Grande
    ## 84      1804        Hector Aragones Frutos 451.00      60  Camion Grande
    ## 85       200              Felipe Villatoro  50.00      60          Panel
    ## 86       377              Felipe Villatoro  94.25      90          Panel
    ## 87      1673          Pedro Alvarez Parejo 418.25      90  Camion Grande
    ## 88      1640          Angel Valdez Alegria 410.00      60  Camion Grande
    ## 89       623       Fernando Mariano Berrio 155.75      30 Camion Pequeño
    ## 90       870       Fernando Mariano Berrio 217.50      30 Camion Pequeño
    ## 91       233          Pedro Alvarez Parejo  58.25      30          Panel
    ## 92       894       Fernando Mariano Berrio 223.50      30 Camion Pequeño
    ## 93       207          Angel Valdez Alegria  51.75      60          Panel
    ## 94      1472 Juan Francisco Portillo Gomez 368.00      30  Camion Grande
    ## 95       643        Hector Aragones Frutos 160.75      30 Camion Pequeño
    ## 96       961       Fernando Mariano Berrio 240.25      60 Camion Pequeño
    ## 97      1557 Juan Francisco Portillo Gomez 389.25      60  Camion Grande
    ## 98      1273          Angel Valdez Alegria 318.25      90  Camion Grande
    ## 99       398              Felipe Villatoro  99.50      30          Panel
    ## 100      986      Ismael Rodero Monteagudo 246.50      30 Camion Pequeño
    ## 101     1569                  Hector Giron 392.25      90  Camion Grande
    ## 102     1795       Fernando Mariano Berrio 448.75      30  Camion Grande
    ## 103     1838 Juan Francisco Portillo Gomez 459.50      30  Camion Grande
    ## 104     1151        Hector Aragones Frutos 287.75      30  Camion Grande
    ## 105      304             Luis Jaime Urbano  76.00      90          Panel
    ## 106      247                  Hector Giron  61.75      90          Panel
    ## 107     1579             Luis Jaime Urbano 394.75      60  Camion Grande
    ## 108     1727          Pedro Alvarez Parejo 431.75      90  Camion Grande
    ## 109      801 Juan Francisco Portillo Gomez 200.25      60 Camion Pequeño
    ## 110     1458       Fernando Mariano Berrio 364.50      30  Camion Grande
    ## 111      687                  Hector Giron 171.75      60 Camion Pequeño
    ## 112      503        Hector Aragones Frutos 125.75      30 Camion Pequeño
    ## 113      683             Luis Jaime Urbano 170.75      30 Camion Pequeño
    ## 114     1427                  Hector Giron 356.75      90  Camion Grande
    ## 115     1013          Pedro Alvarez Parejo 253.25      30  Camion Grande
    ## 116     1720          Angel Valdez Alegria 430.00      30  Camion Grande
    ## 117      770                  Hector Giron 192.50      30 Camion Pequeño
    ## 118     1934 Juan Francisco Portillo Gomez 483.50      90  Camion Grande
    ## 119      743          Pedro Alvarez Parejo 185.75      60 Camion Pequeño
    ## 120     1850              Felipe Villatoro 462.50      30  Camion Grande
    ## 121      875              Felipe Villatoro 218.75      30 Camion Pequeño
    ## 122     1919        Hector Aragones Frutos 479.75      90  Camion Grande
    ## 123     1073       Fernando Mariano Berrio 268.25      30  Camion Grande
    ## 124      902        Hector Aragones Frutos 225.50      60 Camion Pequeño
    ## 125      203                  Hector Giron  50.75      60          Panel
    ## 126      659       Fernando Mariano Berrio 164.75      60 Camion Pequeño
    ## 127     1204              Felipe Villatoro 301.00      30  Camion Grande
    ## 128     1967             Luis Jaime Urbano 491.75      30  Camion Grande
    ## 129     1837      Ismael Rodero Monteagudo 459.25      90  Camion Grande
    ## 130      681          Pedro Alvarez Parejo 170.25      90 Camion Pequeño
    ## 131      451 Juan Francisco Portillo Gomez 112.75      30          Panel
    ## 132     1670             Luis Jaime Urbano 417.50      90  Camion Grande
    ## 133     1986        Hector Aragones Frutos 496.50      60  Camion Grande
    ## 134     1091        Hector Aragones Frutos 272.75      90  Camion Grande
    ## 135     1302          Angel Valdez Alegria 325.50      60  Camion Grande
    ## 136     1779      Ismael Rodero Monteagudo 444.75      30  Camion Grande
    ## 137      970 Juan Francisco Portillo Gomez 242.50      60 Camion Pequeño
    ## 138     1766          Pedro Alvarez Parejo 441.50      60  Camion Grande
    ## 139     1062 Juan Francisco Portillo Gomez 265.50      60  Camion Grande
    ## 140     1804          Angel Valdez Alegria 451.00      30  Camion Grande
    ## 141     1440          Pedro Alvarez Parejo 360.00      30  Camion Grande
    ## 142     1353                  Hector Giron 338.25      90  Camion Grande
    ## 143     1144      Ismael Rodero Monteagudo 286.00      30  Camion Grande
    ## 144     1366          Pedro Alvarez Parejo 341.50      30  Camion Grande
    ## 145      228 Juan Francisco Portillo Gomez  57.00      30          Panel
    ## 146      247          Pedro Alvarez Parejo  61.75      90          Panel
    ## 147     1152                  Hector Giron 288.00      30  Camion Grande
    ## 148      758       Fernando Mariano Berrio 189.50      90 Camion Pequeño
    ## 149      813 Juan Francisco Portillo Gomez 203.25      60 Camion Pequeño
    ## 150     1598        Hector Aragones Frutos 399.50      30  Camion Grande
    ## 151     1379 Juan Francisco Portillo Gomez 344.75      90  Camion Grande
    ## 152     1258             Luis Jaime Urbano 314.50      60  Camion Grande
    ## 153     1564        Hector Aragones Frutos 391.00      30  Camion Grande
    ## 154     1626          Angel Valdez Alegria 406.50      60  Camion Grande
    ## 155     1866              Felipe Villatoro 466.50      90  Camion Grande
    ## 156      619          Angel Valdez Alegria 154.75      90 Camion Pequeño
    ## 157     1130       Fernando Mariano Berrio 282.50      90  Camion Grande
    ## 158     1623          Pedro Alvarez Parejo 405.75      60  Camion Grande
    ## 159     1981             Luis Jaime Urbano 495.25      30  Camion Grande
    ## 160      601       Fernando Mariano Berrio 150.25      30 Camion Pequeño
    ## 161      428        Hector Aragones Frutos 107.00      60          Panel
    ## 162      259          Angel Valdez Alegria  64.75      90          Panel
    ## 163     1767             Luis Jaime Urbano 441.75      30  Camion Grande
    ## 164     1213        Hector Aragones Frutos 303.25      60  Camion Grande
    ## 165      866 Juan Francisco Portillo Gomez 216.50      60 Camion Pequeño
    ## 166     1118          Angel Valdez Alegria 279.50      60  Camion Grande
    ## 167     1397          Angel Valdez Alegria 349.25      60  Camion Grande
    ## 168     1125       Fernando Mariano Berrio 281.25      30  Camion Grande
    ## 169     1904       Fernando Mariano Berrio 476.00      90  Camion Grande
    ## 170      496                  Hector Giron 124.00      60          Panel
    ## 171     1064      Ismael Rodero Monteagudo 266.00      90  Camion Grande
    ## 172     1100 Juan Francisco Portillo Gomez 275.00      90  Camion Grande
    ## 173     1010 Juan Francisco Portillo Gomez 252.50      60  Camion Grande
    ## 174     1174      Ismael Rodero Monteagudo 293.50      30  Camion Grande
    ## 175      941          Pedro Alvarez Parejo 235.25      60 Camion Pequeño
    ## 176      988          Pedro Alvarez Parejo 247.00      30 Camion Pequeño
    ## 177     1636       Fernando Mariano Berrio 409.00      30  Camion Grande
    ## 178     1401                  Hector Giron 350.25      30  Camion Grande
    ## 179     1854          Pedro Alvarez Parejo 463.50      90  Camion Grande
    ## 180      836 Juan Francisco Portillo Gomez 209.00      90 Camion Pequeño
    ## 181     1302          Pedro Alvarez Parejo 325.50      90  Camion Grande
    ## 182      235 Juan Francisco Portillo Gomez  58.75      30          Panel
    ## 183      977                  Hector Giron 244.25      30 Camion Pequeño
    ## 184     1970              Felipe Villatoro 492.50      60  Camion Grande
    ## 185      413          Pedro Alvarez Parejo 103.25      60          Panel
    ## 186     1573       Fernando Mariano Berrio 393.25      30  Camion Grande
    ## 187     1564 Juan Francisco Portillo Gomez 391.00      90  Camion Grande
    ## 188      908          Pedro Alvarez Parejo 227.00      60 Camion Pequeño
    ## 189     1727        Hector Aragones Frutos 431.75      90  Camion Grande
    ## 190     1774 Juan Francisco Portillo Gomez 443.50      30  Camion Grande
    ## 191     1476                  Hector Giron 369.00      30  Camion Grande
    ## 192      701       Fernando Mariano Berrio 175.25      60 Camion Pequeño
    ## 193      808          Pedro Alvarez Parejo 202.00      90 Camion Pequeño
    ## 194      995             Luis Jaime Urbano 248.75      60 Camion Pequeño
    ## 195     1743 Juan Francisco Portillo Gomez 435.75      90  Camion Grande
    ## 196      883       Fernando Mariano Berrio 220.75      90 Camion Pequeño
    ## 197     1062          Angel Valdez Alegria 265.50      90  Camion Grande
    ##     mes anio
    ## 1    11 2018
    ## 2    11 2018
    ## 3    11 2018
    ## 4    11 2018
    ## 5    11 2018
    ## 6    11 2018
    ## 7    11 2018
    ## 8    11 2018
    ## 9    11 2018
    ## 10   11 2018
    ## 11   11 2018
    ## 12   11 2018
    ## 13   11 2018
    ## 14   11 2018
    ## 15   11 2018
    ## 16   11 2018
    ## 17   11 2018
    ## 18   11 2018
    ## 19   11 2018
    ## 20   11 2018
    ## 21   11 2018
    ## 22   11 2018
    ## 23   11 2018
    ## 24   11 2018
    ## 25   11 2018
    ## 26   11 2018
    ## 27   11 2018
    ## 28   11 2018
    ## 29   11 2018
    ## 30   11 2018
    ## 31   11 2018
    ## 32   11 2018
    ## 33   11 2018
    ## 34   11 2018
    ## 35   11 2018
    ## 36   11 2018
    ## 37   11 2018
    ## 38   11 2018
    ## 39   11 2018
    ## 40   11 2018
    ## 41   11 2018
    ## 42   11 2018
    ## 43   11 2018
    ## 44   11 2018
    ## 45   11 2018
    ## 46   11 2018
    ## 47   11 2018
    ## 48   11 2018
    ## 49   11 2018
    ## 50   11 2018
    ## 51   11 2018
    ## 52   11 2018
    ## 53   11 2018
    ## 54   11 2018
    ## 55   11 2018
    ## 56   11 2018
    ## 57   11 2018
    ## 58   11 2018
    ## 59   11 2018
    ## 60   11 2018
    ## 61   11 2018
    ## 62   11 2018
    ## 63   11 2018
    ## 64   11 2018
    ## 65   11 2018
    ## 66   11 2018
    ## 67   11 2018
    ## 68   11 2018
    ## 69   11 2018
    ## 70   11 2018
    ## 71   11 2018
    ## 72   11 2018
    ## 73   11 2018
    ## 74   11 2018
    ## 75   11 2018
    ## 76   11 2018
    ## 77   11 2018
    ## 78   11 2018
    ## 79   11 2018
    ## 80   11 2018
    ## 81   11 2018
    ## 82   11 2018
    ## 83   11 2018
    ## 84   11 2018
    ## 85   11 2018
    ## 86   11 2018
    ## 87   11 2018
    ## 88   11 2018
    ## 89   11 2018
    ## 90   11 2018
    ## 91   11 2018
    ## 92   11 2018
    ## 93   11 2018
    ## 94   11 2018
    ## 95   11 2018
    ## 96   11 2018
    ## 97   11 2018
    ## 98   11 2018
    ## 99   11 2018
    ## 100  11 2018
    ## 101  11 2018
    ## 102  11 2018
    ## 103  11 2018
    ## 104  11 2018
    ## 105  11 2018
    ## 106  11 2018
    ## 107  11 2018
    ## 108  11 2018
    ## 109  11 2018
    ## 110  11 2018
    ## 111  11 2018
    ## 112  11 2018
    ## 113  11 2018
    ## 114  11 2018
    ## 115  11 2018
    ## 116  11 2018
    ## 117  11 2018
    ## 118  11 2018
    ## 119  11 2018
    ## 120  11 2018
    ## 121  11 2018
    ## 122  11 2018
    ## 123  11 2018
    ## 124  11 2018
    ## 125  11 2018
    ## 126  11 2018
    ## 127  11 2018
    ## 128  11 2018
    ## 129  11 2018
    ## 130  11 2018
    ## 131  11 2018
    ## 132  11 2018
    ## 133  11 2018
    ## 134  11 2018
    ## 135  11 2018
    ## 136  11 2018
    ## 137  11 2018
    ## 138  11 2018
    ## 139  11 2018
    ## 140  11 2018
    ## 141  11 2018
    ## 142  11 2018
    ## 143  11 2018
    ## 144  11 2018
    ## 145  11 2018
    ## 146  11 2018
    ## 147  11 2018
    ## 148  11 2018
    ## 149  11 2018
    ## 150  11 2018
    ## 151  11 2018
    ## 152  11 2018
    ## 153  11 2018
    ## 154  11 2018
    ## 155  11 2018
    ## 156  11 2018
    ## 157  11 2018
    ## 158  11 2018
    ## 159  11 2018
    ## 160  11 2018
    ## 161  11 2018
    ## 162  11 2018
    ## 163  11 2018
    ## 164  11 2018
    ## 165  11 2018
    ## 166  11 2018
    ## 167  11 2018
    ## 168  11 2018
    ## 169  11 2018
    ## 170  11 2018
    ## 171  11 2018
    ## 172  11 2018
    ## 173  11 2018
    ## 174  11 2018
    ## 175  11 2018
    ## 176  11 2018
    ## 177  11 2018
    ## 178  11 2018
    ## 179  11 2018
    ## 180  11 2018
    ## 181  11 2018
    ## 182  11 2018
    ## 183  11 2018
    ## 184  11 2018
    ## 185  11 2018
    ## 186  11 2018
    ## 187  11 2018
    ## 188  11 2018
    ## 189  11 2018
    ## 190  11 2018
    ## 191  11 2018
    ## 192  11 2018
    ## 193  11 2018
    ## 194  11 2018
    ## 195  11 2018
    ## 196  11 2018
    ## 197  11 2018

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
df1 <- bind_rows(lab1)
df1
```

    ##      COD_VIAJE                                            CLIENTE
    ## 1     10000001            EL PINCHE OBELISCO / Despacho a cliente
    ## 2     10000002                    TAQUERIA EL CHINITO |||Faltante
    ## 3     10000003           TIENDA LA BENDICION / Despacho a cliente
    ## 4     10000004                                TAQUERIA EL CHINITO
    ## 5     10000005      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 6     10000006                            UBIQUO LABS |||FALTANTE
    ## 7     10000007      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 8     10000008                    TAQUERIA EL CHINITO |||Faltante
    ## 9     10000009                       EL GALLO NEGRO |||DEVOLUCION
    ## 10    10000010      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 11    10000011                EL GALLO NEGRO / Despacho a cliente
    ## 12    10000012 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 13    10000013                          POLLO PINULITO|||FALTANTE
    ## 14    10000014                EL GALLO NEGRO / Despacho a cliente
    ## 15    10000015                                TAQUERIA EL CHINITO
    ## 16    10000016            EL PINCHE OBELISCO / Despacho a cliente
    ## 17    10000017        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 18    10000018           TIENDA LA BENDICION / Despacho a cliente
    ## 19    10000019           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 20    10000020                                        UBIQUO LABS
    ## 21    10000021           TIENDA LA BENDICION / Despacho a cliente
    ## 22    10000022                                     BAR LA OFICINA
    ## 23    10000023                            UBIQUO LABS |||FALTANTE
    ## 24    10000024           TIENDA LA BENDICION / Despacho a cliente
    ## 25    10000025           TIENDA LA BENDICION / Despacho a cliente
    ## 26    10000026      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 27    10000027            ABARROTERIA EBENEZER/Despacho a cliente
    ## 28    10000028        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 29    10000029           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 30    10000030                                TAQUERIA EL CHINITO
    ## 31    10000031            ABARROTERIA EBENEZER/Despacho a cliente
    ## 32    10000032                                TAQUERIA EL CHINITO
    ## 33    10000033                     EL PINCHE OBELISCO |||Faltante
    ## 34    10000034                                        UBIQUO LABS
    ## 35    10000035 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 36    10000036                            UBIQUO LABS |||FALTANTE
    ## 37    10000037                     EL PINCHE OBELISCO |||Faltante
    ## 38    10000038        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 39    10000039            ABARROTERIA EBENEZER/Despacho a cliente
    ## 40    10000040                                TAQUERIA EL CHINITO
    ## 41    10000041 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 42    10000042                            UBIQUO LABS |||FALTANTE
    ## 43    10000043           TIENDA LA BENDICION / Despacho a cliente
    ## 44    10000044            ABARROTERIA EBENEZER/Despacho a cliente
    ## 45    10000045           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 46    10000046           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 47    10000047                       EL GALLO NEGRO |||DEVOLUCION
    ## 48    10000048        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 49    10000049                  POLLO PINULITO/Despacho a cliente
    ## 50    10000050           TIENDA LA BENDICION / Despacho a cliente
    ## 51    10000051                              HOSPITAL LAS AMERICAS
    ## 52    10000052                                     BAR LA OFICINA
    ## 53    10000053                EL GALLO NEGRO / Despacho a cliente
    ## 54    10000054            ABARROTERIA EBENEZER/Despacho a cliente
    ## 55    10000055                  POLLO PINULITO/Despacho a cliente
    ## 56    10000056                                     BAR LA OFICINA
    ## 57    10000057                     EL PINCHE OBELISCO |||Faltante
    ## 58    10000058                                        UBIQUO LABS
    ## 59    10000059           TIENDA LA BENDICION / Despacho a cliente
    ## 60    10000060                                     BAR LA OFICINA
    ## 61    10000061                                     BAR LA OFICINA
    ## 62    10000062                                TAQUERIA EL CHINITO
    ## 63    10000063 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 64    10000064                          POLLO PINULITO|||FALTANTE
    ## 65    10000065                       EL GALLO NEGRO |||DEVOLUCION
    ## 66    10000066                                     BAR LA OFICINA
    ## 67    10000067                                        UBIQUO LABS
    ## 68    10000068                                TAQUERIA EL CHINITO
    ## 69    10000069                    TAQUERIA EL CHINITO |||Faltante
    ## 70    10000070                    TAQUERIA EL CHINITO |||Faltante
    ## 71    10000071                     EL PINCHE OBELISCO |||Faltante
    ## 72    10000072                                     BAR LA OFICINA
    ## 73    10000073                     EL PINCHE OBELISCO |||Faltante
    ## 74    10000074                     EL PINCHE OBELISCO |||Faltante
    ## 75    10000075                                     BAR LA OFICINA
    ## 76    10000076                EL GALLO NEGRO / Despacho a cliente
    ## 77    10000077            ABARROTERIA EBENEZER/Despacho a cliente
    ## 78    10000078        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 79    10000079 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 80    10000080                    TAQUERIA EL CHINITO |||Faltante
    ## 81    10000081           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 82    10000082 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 83    10000083           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 84    10000084            EL PINCHE OBELISCO / Despacho a cliente
    ## 85    10000085           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 86    10000086                     EL PINCHE OBELISCO |||Faltante
    ## 87    10000087 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 88    10000088                EL GALLO NEGRO / Despacho a cliente
    ## 89    10000089            EL PINCHE OBELISCO / Despacho a cliente
    ## 90    10000090                          POLLO PINULITO|||FALTANTE
    ## 91    10000091 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 92    10000092        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 93    10000093                                     BAR LA OFICINA
    ## 94    10000094                  POLLO PINULITO/Despacho a cliente
    ## 95    10000095           TIENDA LA BENDICION / Despacho a cliente
    ## 96    10000096      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 97    10000097                                        UBIQUO LABS
    ## 98    10000098                  POLLO PINULITO/Despacho a cliente
    ## 99    10000099                     EL PINCHE OBELISCO |||Faltante
    ## 100   10000100                                     BAR LA OFICINA
    ## 101   10000101                     EL PINCHE OBELISCO |||Faltante
    ## 102   10000102                          POLLO PINULITO|||FALTANTE
    ## 103   10000103                    TAQUERIA EL CHINITO |||Faltante
    ## 104   10000104            EL PINCHE OBELISCO / Despacho a cliente
    ## 105   10000105                    TAQUERIA EL CHINITO |||Faltante
    ## 106   10000106        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 107   10000107 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 108   10000108 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 109   10000109                                        UBIQUO LABS
    ## 110   10000110                       EL GALLO NEGRO |||DEVOLUCION
    ## 111   10000111      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 112   10000112            EL PINCHE OBELISCO / Despacho a cliente
    ## 113   10000113                                TAQUERIA EL CHINITO
    ## 114   10000114           TIENDA LA BENDICION / Despacho a cliente
    ## 115   10000115                              HOSPITAL LAS AMERICAS
    ## 116   10000116                EL GALLO NEGRO / Despacho a cliente
    ## 117   10000117           TIENDA LA BENDICION / Despacho a cliente
    ## 118   10000118            EL PINCHE OBELISCO / Despacho a cliente
    ## 119   10000119           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 120   10000120                                TAQUERIA EL CHINITO
    ## 121   10000121                                        UBIQUO LABS
    ## 122   10000122                     EL PINCHE OBELISCO |||Faltante
    ## 123   10000123 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 124   10000124                       EL GALLO NEGRO |||DEVOLUCION
    ## 125   10000125                          POLLO PINULITO|||FALTANTE
    ## 126   10000126                  POLLO PINULITO/Despacho a cliente
    ## 127   10000127                                TAQUERIA EL CHINITO
    ## 128   10000128                  POLLO PINULITO/Despacho a cliente
    ## 129   10000129            ABARROTERIA EBENEZER/Despacho a cliente
    ## 130   10000130 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 131   10000131                                     BAR LA OFICINA
    ## 132   10000132                     EL PINCHE OBELISCO |||Faltante
    ## 133   10000133                          POLLO PINULITO|||FALTANTE
    ## 134   10000134 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 135   10000135                       EL GALLO NEGRO |||DEVOLUCION
    ## 136   10000136                     EL PINCHE OBELISCO |||Faltante
    ## 137   10000137           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 138   10000138                    TAQUERIA EL CHINITO |||Faltante
    ## 139   10000139            EL PINCHE OBELISCO / Despacho a cliente
    ## 140   10000140                                     BAR LA OFICINA
    ## 141   10000141                     EL PINCHE OBELISCO |||Faltante
    ## 142   10000142        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 143   10000143        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 144   10000144        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 145   10000145 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 146   10000146                    TAQUERIA EL CHINITO |||Faltante
    ## 147   10000147                     EL PINCHE OBELISCO |||Faltante
    ## 148   10000148                                        UBIQUO LABS
    ## 149   10000149                                TAQUERIA EL CHINITO
    ## 150   10000150            ABARROTERIA EBENEZER/Despacho a cliente
    ## 151   10000151      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 152   10000152                                TAQUERIA EL CHINITO
    ## 153   10000153        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 154   10000154 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 155   10000155                    TAQUERIA EL CHINITO |||Faltante
    ## 156   10000156            EL PINCHE OBELISCO / Despacho a cliente
    ## 157   10000157                  POLLO PINULITO/Despacho a cliente
    ## 158   10000158                     EL PINCHE OBELISCO |||Faltante
    ## 159   10000159                                     BAR LA OFICINA
    ## 160   10000160            EL PINCHE OBELISCO / Despacho a cliente
    ## 161   10000161        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 162   10000162                       EL GALLO NEGRO |||DEVOLUCION
    ## 163   10000163            EL PINCHE OBELISCO / Despacho a cliente
    ## 164   10000164                EL GALLO NEGRO / Despacho a cliente
    ## 165   10000165                                TAQUERIA EL CHINITO
    ## 166   10000166                                     BAR LA OFICINA
    ## 167   10000167        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 168   10000168                     EL PINCHE OBELISCO |||Faltante
    ## 169   10000169 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 170   10000170                            UBIQUO LABS |||FALTANTE
    ## 171   10000171                  POLLO PINULITO/Despacho a cliente
    ## 172   10000172                    TAQUERIA EL CHINITO |||Faltante
    ## 173   10000173        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 174   10000174                       EL GALLO NEGRO |||DEVOLUCION
    ## 175   10000175                                TAQUERIA EL CHINITO
    ## 176   10000176                                TAQUERIA EL CHINITO
    ## 177   10000177                            UBIQUO LABS |||FALTANTE
    ## 178   10000178        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 179   10000179                                TAQUERIA EL CHINITO
    ## 180   10000180                                TAQUERIA EL CHINITO
    ## 181   10000181                          POLLO PINULITO|||FALTANTE
    ## 182   10000182            ABARROTERIA EBENEZER/Despacho a cliente
    ## 183   10000183           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 184   10000184                                     BAR LA OFICINA
    ## 185   10000185           TIENDA LA BENDICION / Despacho a cliente
    ## 186   10000186                                        UBIQUO LABS
    ## 187   10000187                                        UBIQUO LABS
    ## 188   10000188           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 189   10000189                                TAQUERIA EL CHINITO
    ## 190   10000190        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 191   10000191                                TAQUERIA EL CHINITO
    ## 192   10000192            ABARROTERIA EBENEZER/Despacho a cliente
    ## 193   10000193        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 194   10000194                    TAQUERIA EL CHINITO |||Faltante
    ## 195   10000195                       EL GALLO NEGRO |||DEVOLUCION
    ## 196   10000196           TIENDA LA BENDICION / Despacho a cliente
    ## 197   10000197                          POLLO PINULITO|||FALTANTE
    ## 198   10000198                          POLLO PINULITO|||FALTANTE
    ## 199   10000199                                TAQUERIA EL CHINITO
    ## 200   10000200                     EL PINCHE OBELISCO |||Faltante
    ## 201   10000201                       EL GALLO NEGRO |||DEVOLUCION
    ## 202   10000202           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 203   10000203                     EL PINCHE OBELISCO |||Faltante
    ## 204   10000204                  POLLO PINULITO/Despacho a cliente
    ## 205   10000205            ABARROTERIA EBENEZER/Despacho a cliente
    ## 206   10000206        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 207   10000207                  POLLO PINULITO/Despacho a cliente
    ## 208   10000208            ABARROTERIA EBENEZER/Despacho a cliente
    ## 209   10000209                    TAQUERIA EL CHINITO |||Faltante
    ## 210   10000210            ABARROTERIA EBENEZER/Despacho a cliente
    ## 211   10000211      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 212   10000212      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 213   10000213           TIENDA LA BENDICION / Despacho a cliente
    ## 214   10000214                    TAQUERIA EL CHINITO |||Faltante
    ## 215   10000215           TIENDA LA BENDICION / Despacho a cliente
    ## 216   10000216                                TAQUERIA EL CHINITO
    ## 217   10000217           TIENDA LA BENDICION / Despacho a cliente
    ## 218   10000218                          POLLO PINULITO|||FALTANTE
    ## 219   10000219                                        UBIQUO LABS
    ## 220   10000220                                     BAR LA OFICINA
    ## 221   10000221                    TAQUERIA EL CHINITO |||Faltante
    ## 222   10000222                       EL GALLO NEGRO |||DEVOLUCION
    ## 223   10000223      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 224   10000224                       EL GALLO NEGRO |||DEVOLUCION
    ## 225   10000225 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 226   10000226            EL PINCHE OBELISCO / Despacho a cliente
    ## 227   10000227                EL GALLO NEGRO / Despacho a cliente
    ## 228   10000228           TIENDA LA BENDICION / Despacho a cliente
    ## 229   10000229                    TAQUERIA EL CHINITO |||Faltante
    ## 230   10000230           TIENDA LA BENDICION / Despacho a cliente
    ## 231   10000231                                     BAR LA OFICINA
    ## 232   10000232            ABARROTERIA EBENEZER/Despacho a cliente
    ## 233   10000233                                        UBIQUO LABS
    ## 234   10000234            EL PINCHE OBELISCO / Despacho a cliente
    ## 235   10000235        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 236   10000236                                     BAR LA OFICINA
    ## 237   10000237           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 238   10000238                                        UBIQUO LABS
    ## 239   10000239        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 240   10000240                     EL PINCHE OBELISCO |||Faltante
    ## 241   10000241                                     BAR LA OFICINA
    ## 242   10000242                                TAQUERIA EL CHINITO
    ## 243   10000243            ABARROTERIA EBENEZER/Despacho a cliente
    ## 244   10000244                EL GALLO NEGRO / Despacho a cliente
    ## 245   10000245                                TAQUERIA EL CHINITO
    ## 246   10000246                            UBIQUO LABS |||FALTANTE
    ## 247   10000247           TIENDA LA BENDICION / Despacho a cliente
    ## 248   10000248            ABARROTERIA EBENEZER/Despacho a cliente
    ## 249   10000249      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 250   10000250                          POLLO PINULITO|||FALTANTE
    ## 251   10000251                       EL GALLO NEGRO |||DEVOLUCION
    ## 252   10000252      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 253   10000253      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 254   10000254 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 255   10000255                          POLLO PINULITO|||FALTANTE
    ## 256   10000256 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 257   10000257                       EL GALLO NEGRO |||DEVOLUCION
    ## 258   10000258           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 259   10000259                       EL GALLO NEGRO |||DEVOLUCION
    ## 260   10000260                          POLLO PINULITO|||FALTANTE
    ## 261   10000261                                        UBIQUO LABS
    ## 262   10000262            ABARROTERIA EBENEZER/Despacho a cliente
    ## 263   10000263                       EL GALLO NEGRO |||DEVOLUCION
    ## 264   10000264                     EL PINCHE OBELISCO |||Faltante
    ## 265   10000265            ABARROTERIA EBENEZER/Despacho a cliente
    ## 266   10000266           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 267   10000267           TIENDA LA BENDICION / Despacho a cliente
    ## 268   10000268                            UBIQUO LABS |||FALTANTE
    ## 269   10000269 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 270   10000270 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 271   10000271 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 272   10000272           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 273   10000273                    TAQUERIA EL CHINITO |||Faltante
    ## 274   10000274                EL GALLO NEGRO / Despacho a cliente
    ## 275   10000275                          POLLO PINULITO|||FALTANTE
    ## 276   10000276                                     BAR LA OFICINA
    ## 277   10000277           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 278   10000278      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 279   10000279                EL GALLO NEGRO / Despacho a cliente
    ## 280   10000280                       EL GALLO NEGRO |||DEVOLUCION
    ## 281   10000281                                TAQUERIA EL CHINITO
    ## 282   10000282                                        UBIQUO LABS
    ## 283   10000283                  POLLO PINULITO/Despacho a cliente
    ## 284   10000284                                TAQUERIA EL CHINITO
    ## 285   10000285            ABARROTERIA EBENEZER/Despacho a cliente
    ## 286   10000286        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 287   10000287           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 288   10000288           TIENDA LA BENDICION / Despacho a cliente
    ## 289   10000289            ABARROTERIA EBENEZER/Despacho a cliente
    ## 290   10000290                                TAQUERIA EL CHINITO
    ## 291   10000291                            UBIQUO LABS |||FALTANTE
    ## 292   10000292      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 293   10000293                          POLLO PINULITO|||FALTANTE
    ## 294   10000294                          POLLO PINULITO|||FALTANTE
    ## 295   10000295                EL GALLO NEGRO / Despacho a cliente
    ## 296   10000296            ABARROTERIA EBENEZER/Despacho a cliente
    ## 297   10000297                     EL PINCHE OBELISCO |||Faltante
    ## 298   10000298            EL PINCHE OBELISCO / Despacho a cliente
    ## 299   10000299            ABARROTERIA EBENEZER/Despacho a cliente
    ## 300   10000300                EL GALLO NEGRO / Despacho a cliente
    ## 301   10000301        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 302   10000302                  POLLO PINULITO/Despacho a cliente
    ## 303   10000303                                        UBIQUO LABS
    ## 304   10000304                            UBIQUO LABS |||FALTANTE
    ## 305   10000305                            UBIQUO LABS |||FALTANTE
    ## 306   10000306            ABARROTERIA EBENEZER/Despacho a cliente
    ## 307   10000307            EL PINCHE OBELISCO / Despacho a cliente
    ## 308   10000308           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 309   10000309                            UBIQUO LABS |||FALTANTE
    ## 310   10000310      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 311   10000311                EL GALLO NEGRO / Despacho a cliente
    ## 312   10000312                    TAQUERIA EL CHINITO |||Faltante
    ## 313   10000313           TIENDA LA BENDICION / Despacho a cliente
    ## 314   10000314                            UBIQUO LABS |||FALTANTE
    ## 315   10000315                                        UBIQUO LABS
    ## 316   10000316                                TAQUERIA EL CHINITO
    ## 317   10000317                                        UBIQUO LABS
    ## 318   10000318           TIENDA LA BENDICION / Despacho a cliente
    ## 319   10000319           TIENDA LA BENDICION / Despacho a cliente
    ## 320   10000320                              HOSPITAL LAS AMERICAS
    ## 321   10000321                            UBIQUO LABS |||FALTANTE
    ## 322   10000322            ABARROTERIA EBENEZER/Despacho a cliente
    ## 323   10000323                              HOSPITAL LAS AMERICAS
    ## 324   10000324 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 325   10000325           TIENDA LA BENDICION / Despacho a cliente
    ## 326   10000326            ABARROTERIA EBENEZER/Despacho a cliente
    ## 327   10000327                              HOSPITAL LAS AMERICAS
    ## 328   10000328                                TAQUERIA EL CHINITO
    ## 329   10000329            EL PINCHE OBELISCO / Despacho a cliente
    ## 330   10000330                                        UBIQUO LABS
    ## 331   10000331                                TAQUERIA EL CHINITO
    ## 332   10000332                                     BAR LA OFICINA
    ## 333   10000333                            UBIQUO LABS |||FALTANTE
    ## 334   10000334            ABARROTERIA EBENEZER/Despacho a cliente
    ## 335   10000335           TIENDA LA BENDICION / Despacho a cliente
    ## 336   10000336                                     BAR LA OFICINA
    ## 337   10000337                       EL GALLO NEGRO |||DEVOLUCION
    ## 338   10000338                  POLLO PINULITO/Despacho a cliente
    ## 339   10000339                                TAQUERIA EL CHINITO
    ## 340   10000340      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 341   10000341                    TAQUERIA EL CHINITO |||Faltante
    ## 342   10000342                              HOSPITAL LAS AMERICAS
    ## 343   10000343            ABARROTERIA EBENEZER/Despacho a cliente
    ## 344   10000344                     EL PINCHE OBELISCO |||Faltante
    ## 345   10000345                  POLLO PINULITO/Despacho a cliente
    ## 346   10000346                                     BAR LA OFICINA
    ## 347   10000347            EL PINCHE OBELISCO / Despacho a cliente
    ## 348   10000348                              HOSPITAL LAS AMERICAS
    ## 349   10000349                          POLLO PINULITO|||FALTANTE
    ## 350   10000350                EL GALLO NEGRO / Despacho a cliente
    ## 351   10000351                  POLLO PINULITO/Despacho a cliente
    ## 352   10000352            ABARROTERIA EBENEZER/Despacho a cliente
    ## 353   10000353                EL GALLO NEGRO / Despacho a cliente
    ## 354   10000354                                TAQUERIA EL CHINITO
    ## 355   10000355            ABARROTERIA EBENEZER/Despacho a cliente
    ## 356   10000356 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 357   10000357                EL GALLO NEGRO / Despacho a cliente
    ## 358   10000358                                        UBIQUO LABS
    ## 359   10000359           TIENDA LA BENDICION / Despacho a cliente
    ## 360   10000360            ABARROTERIA EBENEZER/Despacho a cliente
    ## 361   10000361                                     BAR LA OFICINA
    ## 362   10000362                EL GALLO NEGRO / Despacho a cliente
    ## 363   10000363                              HOSPITAL LAS AMERICAS
    ## 364   10000364                    TAQUERIA EL CHINITO |||Faltante
    ## 365   10000365                    TAQUERIA EL CHINITO |||Faltante
    ## 366   10000366            ABARROTERIA EBENEZER/Despacho a cliente
    ## 367   10000367                            UBIQUO LABS |||FALTANTE
    ## 368   10000368                            UBIQUO LABS |||FALTANTE
    ## 369   10000369                              HOSPITAL LAS AMERICAS
    ## 370   10000370        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 371   10000371                              HOSPITAL LAS AMERICAS
    ## 372   10000372            ABARROTERIA EBENEZER/Despacho a cliente
    ## 373   10000373                     EL PINCHE OBELISCO |||Faltante
    ## 374   10000374                                        UBIQUO LABS
    ## 375   10000375           TIENDA LA BENDICION / Despacho a cliente
    ## 376   10000376                                     BAR LA OFICINA
    ## 377   10000377           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 378   10000378                                        UBIQUO LABS
    ## 379   10000379                          POLLO PINULITO|||FALTANTE
    ## 380   10000380                     EL PINCHE OBELISCO |||Faltante
    ## 381   10000381                            UBIQUO LABS |||FALTANTE
    ## 382   10000382           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 383   10000383            EL PINCHE OBELISCO / Despacho a cliente
    ## 384   10000384 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 385   10000385            EL PINCHE OBELISCO / Despacho a cliente
    ## 386   10000386                       EL GALLO NEGRO |||DEVOLUCION
    ## 387   10000387                            UBIQUO LABS |||FALTANTE
    ## 388   10000388 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 389   10000389        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 390   10000390                     EL PINCHE OBELISCO |||Faltante
    ## 391   10000391 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 392   10000392                     EL PINCHE OBELISCO |||Faltante
    ## 393   10000393           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 394   10000394                            UBIQUO LABS |||FALTANTE
    ## 395   10000395      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 396   10000396            ABARROTERIA EBENEZER/Despacho a cliente
    ## 397   10000397           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 398   10000398 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 399   10000399                                     BAR LA OFICINA
    ## 400   10000400                  POLLO PINULITO/Despacho a cliente
    ## 401   10000401        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 402   10000402                                TAQUERIA EL CHINITO
    ## 403   10000403                  POLLO PINULITO/Despacho a cliente
    ## 404   10000404                              HOSPITAL LAS AMERICAS
    ## 405   10000405 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 406   10000406                EL GALLO NEGRO / Despacho a cliente
    ## 407   10000407                     EL PINCHE OBELISCO |||Faltante
    ## 408   10000408 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 409   10000409        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 410   10000410                  POLLO PINULITO/Despacho a cliente
    ## 411   10000411            EL PINCHE OBELISCO / Despacho a cliente
    ## 412   10000412        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 413   10000413                            UBIQUO LABS |||FALTANTE
    ## 414   10000414                       EL GALLO NEGRO |||DEVOLUCION
    ## 415   10000415                                     BAR LA OFICINA
    ## 416   10000416                                     BAR LA OFICINA
    ## 417   10000417                          POLLO PINULITO|||FALTANTE
    ## 418   10000418            EL PINCHE OBELISCO / Despacho a cliente
    ## 419   10000419                              HOSPITAL LAS AMERICAS
    ## 420   10000420                            UBIQUO LABS |||FALTANTE
    ## 421   10000421 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 422   10000422                          POLLO PINULITO|||FALTANTE
    ## 423   10000423                                TAQUERIA EL CHINITO
    ## 424   10000424                                     BAR LA OFICINA
    ## 425   10000425                EL GALLO NEGRO / Despacho a cliente
    ## 426   10000426      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 427   10000427                                        UBIQUO LABS
    ## 428   10000428                          POLLO PINULITO|||FALTANTE
    ## 429   10000429                                     BAR LA OFICINA
    ## 430   10000430 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 431   10000431        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 432   10000432                       EL GALLO NEGRO |||DEVOLUCION
    ## 433   10000433      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 434   10000434           TIENDA LA BENDICION / Despacho a cliente
    ## 435   10000435                EL GALLO NEGRO / Despacho a cliente
    ## 436   10000436                                TAQUERIA EL CHINITO
    ## 437   10000437                                     BAR LA OFICINA
    ## 438   10000438        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 439   10000439                  POLLO PINULITO/Despacho a cliente
    ## 440   10000440 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 441   10000441 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 442   10000442                EL GALLO NEGRO / Despacho a cliente
    ## 443   10000443      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 444   10000444 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 445   10000445                                     BAR LA OFICINA
    ## 446   10000446                                TAQUERIA EL CHINITO
    ## 447   10000447                                TAQUERIA EL CHINITO
    ## 448   10000448        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 449   10000449                                     BAR LA OFICINA
    ## 450   10000450           TIENDA LA BENDICION / Despacho a cliente
    ## 451   10000451            EL PINCHE OBELISCO / Despacho a cliente
    ## 452   10000452                       EL GALLO NEGRO |||DEVOLUCION
    ## 453   10000453                    TAQUERIA EL CHINITO |||Faltante
    ## 454   10000454      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 455   10000455            ABARROTERIA EBENEZER/Despacho a cliente
    ## 456   10000456                       EL GALLO NEGRO |||DEVOLUCION
    ## 457   10000457           TIENDA LA BENDICION / Despacho a cliente
    ## 458   10000458      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 459   10000459                     EL PINCHE OBELISCO |||Faltante
    ## 460   10000460                     EL PINCHE OBELISCO |||Faltante
    ## 461   10000461 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 462   10000462                     EL PINCHE OBELISCO |||Faltante
    ## 463   10000463                          POLLO PINULITO|||FALTANTE
    ## 464   10000464                                        UBIQUO LABS
    ## 465   10000465                          POLLO PINULITO|||FALTANTE
    ## 466   10000466                                TAQUERIA EL CHINITO
    ## 467   10000467                                        UBIQUO LABS
    ## 468   10000468                    TAQUERIA EL CHINITO |||Faltante
    ## 469   10000469           TIENDA LA BENDICION / Despacho a cliente
    ## 470   10000470                                        UBIQUO LABS
    ## 471   10000471                              HOSPITAL LAS AMERICAS
    ## 472   10000472                                        UBIQUO LABS
    ## 473   10000473        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 474   10000474            ABARROTERIA EBENEZER/Despacho a cliente
    ## 475   10000475                                        UBIQUO LABS
    ## 476   10000476                EL GALLO NEGRO / Despacho a cliente
    ## 477   10000477                EL GALLO NEGRO / Despacho a cliente
    ## 478   10000478           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 479   10000479            EL PINCHE OBELISCO / Despacho a cliente
    ## 480   10000480                EL GALLO NEGRO / Despacho a cliente
    ## 481   10000481                     EL PINCHE OBELISCO |||Faltante
    ## 482   10000482            EL PINCHE OBELISCO / Despacho a cliente
    ## 483   10000483      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 484   10000484            EL PINCHE OBELISCO / Despacho a cliente
    ## 485   10000485                  POLLO PINULITO/Despacho a cliente
    ## 486   10000486            EL PINCHE OBELISCO / Despacho a cliente
    ## 487   10000487            ABARROTERIA EBENEZER/Despacho a cliente
    ## 488   10000488                            UBIQUO LABS |||FALTANTE
    ## 489   10000489                EL GALLO NEGRO / Despacho a cliente
    ## 490   10000490                  POLLO PINULITO/Despacho a cliente
    ## 491   10000491            EL PINCHE OBELISCO / Despacho a cliente
    ## 492   10000492                       EL GALLO NEGRO |||DEVOLUCION
    ## 493   10000493           TIENDA LA BENDICION / Despacho a cliente
    ## 494   10000494           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 495   10000495                EL GALLO NEGRO / Despacho a cliente
    ## 496   10000496                                     BAR LA OFICINA
    ## 497   10000497                    TAQUERIA EL CHINITO |||Faltante
    ## 498   10000498                                        UBIQUO LABS
    ## 499   10000499            ABARROTERIA EBENEZER/Despacho a cliente
    ## 500   10000500                          POLLO PINULITO|||FALTANTE
    ## 501   10000501                     EL PINCHE OBELISCO |||Faltante
    ## 502   10000502           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 503   10000503        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 504   10000504                       EL GALLO NEGRO |||DEVOLUCION
    ## 505   10000505                            UBIQUO LABS |||FALTANTE
    ## 506   10000506                                     BAR LA OFICINA
    ## 507   10000507           TIENDA LA BENDICION / Despacho a cliente
    ## 508   10000508                EL GALLO NEGRO / Despacho a cliente
    ## 509   10000509                     EL PINCHE OBELISCO |||Faltante
    ## 510   10000510                EL GALLO NEGRO / Despacho a cliente
    ## 511   10000511                            UBIQUO LABS |||FALTANTE
    ## 512   10000512                                TAQUERIA EL CHINITO
    ## 513   10000513           TIENDA LA BENDICION / Despacho a cliente
    ## 514   10000514                            UBIQUO LABS |||FALTANTE
    ## 515   10000515            ABARROTERIA EBENEZER/Despacho a cliente
    ## 516   10000516            EL PINCHE OBELISCO / Despacho a cliente
    ## 517   10000517                              HOSPITAL LAS AMERICAS
    ## 518   10000518           TIENDA LA BENDICION / Despacho a cliente
    ## 519   10000519                            UBIQUO LABS |||FALTANTE
    ## 520   10000520            EL PINCHE OBELISCO / Despacho a cliente
    ## 521   10000521                                     BAR LA OFICINA
    ## 522   10000522                    TAQUERIA EL CHINITO |||Faltante
    ## 523   10000523            EL PINCHE OBELISCO / Despacho a cliente
    ## 524   10000524                                     BAR LA OFICINA
    ## 525   10000525            ABARROTERIA EBENEZER/Despacho a cliente
    ## 526   10000526            ABARROTERIA EBENEZER/Despacho a cliente
    ## 527   10000527            EL PINCHE OBELISCO / Despacho a cliente
    ## 528   10000528                          POLLO PINULITO|||FALTANTE
    ## 529   10000529                                        UBIQUO LABS
    ## 530   10000530      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 531   10000531                            UBIQUO LABS |||FALTANTE
    ## 532   10000532                            UBIQUO LABS |||FALTANTE
    ## 533   10000533                              HOSPITAL LAS AMERICAS
    ## 534   10000534                     EL PINCHE OBELISCO |||Faltante
    ## 535   10000535                            UBIQUO LABS |||FALTANTE
    ## 536   10000536                    TAQUERIA EL CHINITO |||Faltante
    ## 537   10000537                          POLLO PINULITO|||FALTANTE
    ## 538   10000538           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 539   10000539 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 540   10000540 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 541   10000541                                     BAR LA OFICINA
    ## 542   10000542                  POLLO PINULITO/Despacho a cliente
    ## 543   10000543                EL GALLO NEGRO / Despacho a cliente
    ## 544   10000544      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 545   10000545                          POLLO PINULITO|||FALTANTE
    ## 546   10000546                                        UBIQUO LABS
    ## 547   10000547                    TAQUERIA EL CHINITO |||Faltante
    ## 548   10000548                                     BAR LA OFICINA
    ## 549   10000549           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 550   10000550                                     BAR LA OFICINA
    ## 551   10000551                     EL PINCHE OBELISCO |||Faltante
    ## 552   10000552                     EL PINCHE OBELISCO |||Faltante
    ## 553   10000553                              HOSPITAL LAS AMERICAS
    ## 554   10000554                EL GALLO NEGRO / Despacho a cliente
    ## 555   10000555                                TAQUERIA EL CHINITO
    ## 556   10000556 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 557   10000557                       EL GALLO NEGRO |||DEVOLUCION
    ## 558   10000558            ABARROTERIA EBENEZER/Despacho a cliente
    ## 559   10000559           TIENDA LA BENDICION / Despacho a cliente
    ## 560   10000560                    TAQUERIA EL CHINITO |||Faltante
    ## 561   10000561        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 562   10000562        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 563   10000563           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 564   10000564                          POLLO PINULITO|||FALTANTE
    ## 565   10000565                EL GALLO NEGRO / Despacho a cliente
    ## 566   10000566                EL GALLO NEGRO / Despacho a cliente
    ## 567   10000567                                TAQUERIA EL CHINITO
    ## 568   10000568                  POLLO PINULITO/Despacho a cliente
    ## 569   10000569                       EL GALLO NEGRO |||DEVOLUCION
    ## 570   10000570 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 571   10000571                    TAQUERIA EL CHINITO |||Faltante
    ## 572   10000572                                TAQUERIA EL CHINITO
    ## 573   10000573                EL GALLO NEGRO / Despacho a cliente
    ## 574   10000574        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 575   10000575                                        UBIQUO LABS
    ## 576   10000576                                        UBIQUO LABS
    ## 577   10000577                                TAQUERIA EL CHINITO
    ## 578   10000578 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 579   10000579                          POLLO PINULITO|||FALTANTE
    ## 580   10000580                            UBIQUO LABS |||FALTANTE
    ## 581   10000581      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 582   10000582      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 583   10000583                              HOSPITAL LAS AMERICAS
    ## 584   10000584                            UBIQUO LABS |||FALTANTE
    ## 585   10000585 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 586   10000586            ABARROTERIA EBENEZER/Despacho a cliente
    ## 587   10000587                     EL PINCHE OBELISCO |||Faltante
    ## 588   10000588                                     BAR LA OFICINA
    ## 589   10000589            EL PINCHE OBELISCO / Despacho a cliente
    ## 590   10000590           TIENDA LA BENDICION / Despacho a cliente
    ## 591   10000591            ABARROTERIA EBENEZER/Despacho a cliente
    ## 592   10000592                    TAQUERIA EL CHINITO |||Faltante
    ## 593   10000593                            UBIQUO LABS |||FALTANTE
    ## 594   10000594                       EL GALLO NEGRO |||DEVOLUCION
    ## 595   10000595                                TAQUERIA EL CHINITO
    ## 596   10000596                                        UBIQUO LABS
    ## 597   10000597                  POLLO PINULITO/Despacho a cliente
    ## 598   10000598                     EL PINCHE OBELISCO |||Faltante
    ## 599   10000599                              HOSPITAL LAS AMERICAS
    ## 600   10000600                  POLLO PINULITO/Despacho a cliente
    ## 601   10000601                     EL PINCHE OBELISCO |||Faltante
    ## 602   10000602      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 603   10000603                     EL PINCHE OBELISCO |||Faltante
    ## 604   10000604                                        UBIQUO LABS
    ## 605   10000605                            UBIQUO LABS |||FALTANTE
    ## 606   10000606 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 607   10000607                                     BAR LA OFICINA
    ## 608   10000608                              HOSPITAL LAS AMERICAS
    ## 609   10000609                              HOSPITAL LAS AMERICAS
    ## 610   10000610                                TAQUERIA EL CHINITO
    ## 611   10000611            ABARROTERIA EBENEZER/Despacho a cliente
    ## 612   10000612        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 613   10000613                  POLLO PINULITO/Despacho a cliente
    ## 614   10000614            EL PINCHE OBELISCO / Despacho a cliente
    ## 615   10000615        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 616   10000616                       EL GALLO NEGRO |||DEVOLUCION
    ## 617   10000617                            UBIQUO LABS |||FALTANTE
    ## 618   10000618                                        UBIQUO LABS
    ## 619   10000619                                     BAR LA OFICINA
    ## 620   10000620                                     BAR LA OFICINA
    ## 621   10000621                          POLLO PINULITO|||FALTANTE
    ## 622   10000622                  POLLO PINULITO/Despacho a cliente
    ## 623   10000623           TIENDA LA BENDICION / Despacho a cliente
    ## 624   10000624                                TAQUERIA EL CHINITO
    ## 625   10000625                  POLLO PINULITO/Despacho a cliente
    ## 626   10000626                            UBIQUO LABS |||FALTANTE
    ## 627   10000627                                        UBIQUO LABS
    ## 628   10000628      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 629   10000629           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 630   10000630 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 631   10000631        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 632   10000632 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 633   10000633                          POLLO PINULITO|||FALTANTE
    ## 634   10000634                  POLLO PINULITO/Despacho a cliente
    ## 635   10000635 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 636   10000636            ABARROTERIA EBENEZER/Despacho a cliente
    ## 637   10000637                       EL GALLO NEGRO |||DEVOLUCION
    ## 638   10000638                  POLLO PINULITO/Despacho a cliente
    ## 639   10000639 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 640   10000640            ABARROTERIA EBENEZER/Despacho a cliente
    ## 641   10000641                                     BAR LA OFICINA
    ## 642   10000642                EL GALLO NEGRO / Despacho a cliente
    ## 643   10000643                    TAQUERIA EL CHINITO |||Faltante
    ## 644   10000644                                TAQUERIA EL CHINITO
    ## 645   10000645      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 646   10000646                                        UBIQUO LABS
    ## 647   10000647                                     BAR LA OFICINA
    ## 648   10000648                       EL GALLO NEGRO |||DEVOLUCION
    ## 649   10000649           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 650   10000650                       EL GALLO NEGRO |||DEVOLUCION
    ## 651   10000651                                        UBIQUO LABS
    ## 652   10000652                            UBIQUO LABS |||FALTANTE
    ## 653   10000653                                        UBIQUO LABS
    ## 654   10000654            ABARROTERIA EBENEZER/Despacho a cliente
    ## 655   10000655            EL PINCHE OBELISCO / Despacho a cliente
    ## 656   10000656                  POLLO PINULITO/Despacho a cliente
    ## 657   10000657           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 658   10000658                       EL GALLO NEGRO |||DEVOLUCION
    ## 659   10000659            ABARROTERIA EBENEZER/Despacho a cliente
    ## 660   10000660           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 661   10000661        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 662   10000662           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 663   10000663                EL GALLO NEGRO / Despacho a cliente
    ## 664   10000664                                TAQUERIA EL CHINITO
    ## 665   10000665                                        UBIQUO LABS
    ## 666   10000666        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 667   10000667                EL GALLO NEGRO / Despacho a cliente
    ## 668   10000668                                        UBIQUO LABS
    ## 669   10000669 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 670   10000670                     EL PINCHE OBELISCO |||Faltante
    ## 671   10000671                     EL PINCHE OBELISCO |||Faltante
    ## 672   10000672                    TAQUERIA EL CHINITO |||Faltante
    ## 673   10000673                                TAQUERIA EL CHINITO
    ## 674   10000674 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 675   10000675                     EL PINCHE OBELISCO |||Faltante
    ## 676   10000676        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 677   10000677                              HOSPITAL LAS AMERICAS
    ## 678   10000678                EL GALLO NEGRO / Despacho a cliente
    ## 679   10000679 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 680   10000680            EL PINCHE OBELISCO / Despacho a cliente
    ## 681   10000681                                        UBIQUO LABS
    ## 682   10000682                                        UBIQUO LABS
    ## 683   10000683      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 684   10000684            ABARROTERIA EBENEZER/Despacho a cliente
    ## 685   10000685                     EL PINCHE OBELISCO |||Faltante
    ## 686   10000686                  POLLO PINULITO/Despacho a cliente
    ## 687   10000687                       EL GALLO NEGRO |||DEVOLUCION
    ## 688   10000688            EL PINCHE OBELISCO / Despacho a cliente
    ## 689   10000689        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 690   10000690                       EL GALLO NEGRO |||DEVOLUCION
    ## 691   10000691                EL GALLO NEGRO / Despacho a cliente
    ## 692   10000692                    TAQUERIA EL CHINITO |||Faltante
    ## 693   10000693                                        UBIQUO LABS
    ## 694   10000694                EL GALLO NEGRO / Despacho a cliente
    ## 695   10000695           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 696   10000696                     EL PINCHE OBELISCO |||Faltante
    ## 697   10000697            EL PINCHE OBELISCO / Despacho a cliente
    ## 698   10000698            ABARROTERIA EBENEZER/Despacho a cliente
    ## 699   10000699            EL PINCHE OBELISCO / Despacho a cliente
    ## 700   10000700            EL PINCHE OBELISCO / Despacho a cliente
    ## 701   10000701           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 702   10000702                  POLLO PINULITO/Despacho a cliente
    ## 703   10000703                  POLLO PINULITO/Despacho a cliente
    ## 704   10000704 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 705   10000705                       EL GALLO NEGRO |||DEVOLUCION
    ## 706   10000706                                     BAR LA OFICINA
    ## 707   10000707                    TAQUERIA EL CHINITO |||Faltante
    ## 708   10000708                EL GALLO NEGRO / Despacho a cliente
    ## 709   10000709                  POLLO PINULITO/Despacho a cliente
    ## 710   10000710                                     BAR LA OFICINA
    ## 711   10000711                                        UBIQUO LABS
    ## 712   10000712            EL PINCHE OBELISCO / Despacho a cliente
    ## 713   10000713                       EL GALLO NEGRO |||DEVOLUCION
    ## 714   10000714                       EL GALLO NEGRO |||DEVOLUCION
    ## 715   10000715      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 716   10000716      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 717   10000717                                     BAR LA OFICINA
    ## 718   10000718        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 719   10000719           TIENDA LA BENDICION / Despacho a cliente
    ## 720   10000720                                     BAR LA OFICINA
    ## 721   10000721      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 722   10000722        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 723   10000723           TIENDA LA BENDICION / Despacho a cliente
    ## 724   10000724 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 725   10000725                          POLLO PINULITO|||FALTANTE
    ## 726   10000726                                TAQUERIA EL CHINITO
    ## 727   10000727        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 728   10000728                                        UBIQUO LABS
    ## 729   10000729      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 730   10000730                                        UBIQUO LABS
    ## 731   10000731                     EL PINCHE OBELISCO |||Faltante
    ## 732   10000732                                        UBIQUO LABS
    ## 733   10000733                EL GALLO NEGRO / Despacho a cliente
    ## 734   10000734                                        UBIQUO LABS
    ## 735   10000735                  POLLO PINULITO/Despacho a cliente
    ## 736   10000736                       EL GALLO NEGRO |||DEVOLUCION
    ## 737   10000737        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 738   10000738                       EL GALLO NEGRO |||DEVOLUCION
    ## 739   10000739           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 740   10000740           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 741   10000741      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 742   10000742 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 743   10000743                          POLLO PINULITO|||FALTANTE
    ## 744   10000744                            UBIQUO LABS |||FALTANTE
    ## 745   10000745            EL PINCHE OBELISCO / Despacho a cliente
    ## 746   10000746                                     BAR LA OFICINA
    ## 747   10000747            ABARROTERIA EBENEZER/Despacho a cliente
    ## 748   10000748 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 749   10000749                              HOSPITAL LAS AMERICAS
    ## 750   10000750                            UBIQUO LABS |||FALTANTE
    ## 751   10000751                  POLLO PINULITO/Despacho a cliente
    ## 752   10000752      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 753   10000753 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 754   10000754                    TAQUERIA EL CHINITO |||Faltante
    ## 755   10000755                                TAQUERIA EL CHINITO
    ## 756   10000756                    TAQUERIA EL CHINITO |||Faltante
    ## 757   10000757                                     BAR LA OFICINA
    ## 758   10000758            EL PINCHE OBELISCO / Despacho a cliente
    ## 759   10000759                            UBIQUO LABS |||FALTANTE
    ## 760   10000760                EL GALLO NEGRO / Despacho a cliente
    ## 761   10000761                    TAQUERIA EL CHINITO |||Faltante
    ## 762   10000762           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 763   10000763                                     BAR LA OFICINA
    ## 764   10000764                    TAQUERIA EL CHINITO |||Faltante
    ## 765   10000765 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 766   10000766                EL GALLO NEGRO / Despacho a cliente
    ## 767   10000767                     EL PINCHE OBELISCO |||Faltante
    ## 768   10000768 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 769   10000769                     EL PINCHE OBELISCO |||Faltante
    ## 770   10000770            ABARROTERIA EBENEZER/Despacho a cliente
    ## 771   10000771                       EL GALLO NEGRO |||DEVOLUCION
    ## 772   10000772        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 773   10000773                                     BAR LA OFICINA
    ## 774   10000774                                     BAR LA OFICINA
    ## 775   10000775                     EL PINCHE OBELISCO |||Faltante
    ## 776   10000776            ABARROTERIA EBENEZER/Despacho a cliente
    ## 777   10000777                       EL GALLO NEGRO |||DEVOLUCION
    ## 778   10000778      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 779   10000779        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 780   10000780                EL GALLO NEGRO / Despacho a cliente
    ## 781   10000781                                        UBIQUO LABS
    ## 782   10000782                            UBIQUO LABS |||FALTANTE
    ## 783   10000783                  POLLO PINULITO/Despacho a cliente
    ## 784   10000784            EL PINCHE OBELISCO / Despacho a cliente
    ## 785   10000785                EL GALLO NEGRO / Despacho a cliente
    ## 786   10000786                    TAQUERIA EL CHINITO |||Faltante
    ## 787   10000787        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 788   10000788                              HOSPITAL LAS AMERICAS
    ## 789   10000789                            UBIQUO LABS |||FALTANTE
    ## 790   10000790                  POLLO PINULITO/Despacho a cliente
    ## 791   10000791 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 792   10000792                              HOSPITAL LAS AMERICAS
    ## 793   10000793           TIENDA LA BENDICION / Despacho a cliente
    ## 794   10000794                            UBIQUO LABS |||FALTANTE
    ## 795   10000795                       EL GALLO NEGRO |||DEVOLUCION
    ## 796   10000796                              HOSPITAL LAS AMERICAS
    ## 797   10000797                              HOSPITAL LAS AMERICAS
    ## 798   10000798           TIENDA LA BENDICION / Despacho a cliente
    ## 799   10000799                EL GALLO NEGRO / Despacho a cliente
    ## 800   10000800                EL GALLO NEGRO / Despacho a cliente
    ## 801   10000801                       EL GALLO NEGRO |||DEVOLUCION
    ## 802   10000802                EL GALLO NEGRO / Despacho a cliente
    ## 803   10000803           TIENDA LA BENDICION / Despacho a cliente
    ## 804   10000804                                TAQUERIA EL CHINITO
    ## 805   10000805 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 806   10000806                            UBIQUO LABS |||FALTANTE
    ## 807   10000807                              HOSPITAL LAS AMERICAS
    ## 808   10000808           TIENDA LA BENDICION / Despacho a cliente
    ## 809   10000809                EL GALLO NEGRO / Despacho a cliente
    ## 810   10000810            ABARROTERIA EBENEZER/Despacho a cliente
    ## 811   10000811                                TAQUERIA EL CHINITO
    ## 812   10000812                     EL PINCHE OBELISCO |||Faltante
    ## 813   10000813                                     BAR LA OFICINA
    ## 814   10000814           TIENDA LA BENDICION / Despacho a cliente
    ## 815   10000815                EL GALLO NEGRO / Despacho a cliente
    ## 816   10000816                  POLLO PINULITO/Despacho a cliente
    ## 817   10000817                EL GALLO NEGRO / Despacho a cliente
    ## 818   10000818      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 819   10000819        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 820   10000820                       EL GALLO NEGRO |||DEVOLUCION
    ## 821   10000821                     EL PINCHE OBELISCO |||Faltante
    ## 822   10000822           TIENDA LA BENDICION / Despacho a cliente
    ## 823   10000823                    TAQUERIA EL CHINITO |||Faltante
    ## 824   10000824                       EL GALLO NEGRO |||DEVOLUCION
    ## 825   10000825                                TAQUERIA EL CHINITO
    ## 826   10000826 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 827   10000827           TIENDA LA BENDICION / Despacho a cliente
    ## 828   10000828                       EL GALLO NEGRO |||DEVOLUCION
    ## 829   10000829                  POLLO PINULITO/Despacho a cliente
    ## 830   10000830            ABARROTERIA EBENEZER/Despacho a cliente
    ## 831   10000831                       EL GALLO NEGRO |||DEVOLUCION
    ## 832   10000832      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 833   10000833                     EL PINCHE OBELISCO |||Faltante
    ## 834   10000834                            UBIQUO LABS |||FALTANTE
    ## 835   10000835      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 836   10000836           TIENDA LA BENDICION / Despacho a cliente
    ## 837   10000837                     EL PINCHE OBELISCO |||Faltante
    ## 838   10000838                                TAQUERIA EL CHINITO
    ## 839   10000839                EL GALLO NEGRO / Despacho a cliente
    ## 840   10000840      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 841   10000841                                     BAR LA OFICINA
    ## 842   10000842                            UBIQUO LABS |||FALTANTE
    ## 843   10000843                                        UBIQUO LABS
    ## 844   10000844            EL PINCHE OBELISCO / Despacho a cliente
    ## 845   10000845        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 846   10000846                     EL PINCHE OBELISCO |||Faltante
    ## 847   10000847                     EL PINCHE OBELISCO |||Faltante
    ## 848   10000848                       EL GALLO NEGRO |||DEVOLUCION
    ## 849   10000849           TIENDA LA BENDICION / Despacho a cliente
    ## 850   10000850      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 851   10000851           TIENDA LA BENDICION / Despacho a cliente
    ## 852   10000852                                        UBIQUO LABS
    ## 853   10000853                              HOSPITAL LAS AMERICAS
    ## 854   10000854            ABARROTERIA EBENEZER/Despacho a cliente
    ## 855   10000855 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 856   10000856      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 857   10000857        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 858   10000858            EL PINCHE OBELISCO / Despacho a cliente
    ## 859   10000859                          POLLO PINULITO|||FALTANTE
    ## 860   10000860      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 861   10000861                     EL PINCHE OBELISCO |||Faltante
    ## 862   10000862        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 863   10000863                    TAQUERIA EL CHINITO |||Faltante
    ## 864   10000864                     EL PINCHE OBELISCO |||Faltante
    ## 865   10000865                EL GALLO NEGRO / Despacho a cliente
    ## 866   10000866 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 867   10000867                EL GALLO NEGRO / Despacho a cliente
    ## 868   10000868           TIENDA LA BENDICION / Despacho a cliente
    ## 869   10000869            ABARROTERIA EBENEZER/Despacho a cliente
    ## 870   10000870        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 871   10000871                    TAQUERIA EL CHINITO |||Faltante
    ## 872   10000872            EL PINCHE OBELISCO / Despacho a cliente
    ## 873   10000873           TIENDA LA BENDICION / Despacho a cliente
    ## 874   10000874                                TAQUERIA EL CHINITO
    ## 875   10000875                                        UBIQUO LABS
    ## 876   10000876                                        UBIQUO LABS
    ## 877   10000877                          POLLO PINULITO|||FALTANTE
    ## 878   10000878                    TAQUERIA EL CHINITO |||Faltante
    ## 879   10000879                            UBIQUO LABS |||FALTANTE
    ## 880   10000880            ABARROTERIA EBENEZER/Despacho a cliente
    ## 881   10000881                                        UBIQUO LABS
    ## 882   10000882                       EL GALLO NEGRO |||DEVOLUCION
    ## 883   10000883                                        UBIQUO LABS
    ## 884   10000884                       EL GALLO NEGRO |||DEVOLUCION
    ## 885   10000885 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 886   10000886                                        UBIQUO LABS
    ## 887   10000887                                     BAR LA OFICINA
    ## 888   10000888                          POLLO PINULITO|||FALTANTE
    ## 889   10000889                    TAQUERIA EL CHINITO |||Faltante
    ## 890   10000890            EL PINCHE OBELISCO / Despacho a cliente
    ## 891   10000891                                TAQUERIA EL CHINITO
    ## 892   10000892                                TAQUERIA EL CHINITO
    ## 893   10000893                          POLLO PINULITO|||FALTANTE
    ## 894   10000894           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 895   10000895                                TAQUERIA EL CHINITO
    ## 896   10000896        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 897   10000897                            UBIQUO LABS |||FALTANTE
    ## 898   10000898                            UBIQUO LABS |||FALTANTE
    ## 899   10000899                     EL PINCHE OBELISCO |||Faltante
    ## 900   10000900 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 901   10000901      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 902   10000902 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 903   10000903      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 904   10000904                            UBIQUO LABS |||FALTANTE
    ## 905   10000905 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 906   10000906                    TAQUERIA EL CHINITO |||Faltante
    ## 907   10000907            EL PINCHE OBELISCO / Despacho a cliente
    ## 908   10000908                                TAQUERIA EL CHINITO
    ## 909   10000909            EL PINCHE OBELISCO / Despacho a cliente
    ## 910   10000910                EL GALLO NEGRO / Despacho a cliente
    ## 911   10000911                       EL GALLO NEGRO |||DEVOLUCION
    ## 912   10000912                    TAQUERIA EL CHINITO |||Faltante
    ## 913   10000913                                     BAR LA OFICINA
    ## 914   10000914                              HOSPITAL LAS AMERICAS
    ## 915   10000915                                TAQUERIA EL CHINITO
    ## 916   10000916                  POLLO PINULITO/Despacho a cliente
    ## 917   10000917                  POLLO PINULITO/Despacho a cliente
    ## 918   10000918 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 919   10000919                                TAQUERIA EL CHINITO
    ## 920   10000920                          POLLO PINULITO|||FALTANTE
    ## 921   10000921 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 922   10000922      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 923   10000923                       EL GALLO NEGRO |||DEVOLUCION
    ## 924   10000924                                     BAR LA OFICINA
    ## 925   10000925            EL PINCHE OBELISCO / Despacho a cliente
    ## 926   10000926           TIENDA LA BENDICION / Despacho a cliente
    ## 927   10000927           TIENDA LA BENDICION / Despacho a cliente
    ## 928   10000928            EL PINCHE OBELISCO / Despacho a cliente
    ## 929   10000929                  POLLO PINULITO/Despacho a cliente
    ## 930   10000930                                        UBIQUO LABS
    ## 931   10000931           TIENDA LA BENDICION / Despacho a cliente
    ## 932   10000932            ABARROTERIA EBENEZER/Despacho a cliente
    ## 933   10000933                                TAQUERIA EL CHINITO
    ## 934   10000934                     EL PINCHE OBELISCO |||Faltante
    ## 935   10000935           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 936   10000936                     EL PINCHE OBELISCO |||Faltante
    ## 937   10000937           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 938   10000938                              HOSPITAL LAS AMERICAS
    ## 939   10000939        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 940   10000940                                     BAR LA OFICINA
    ## 941   10000941 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 942   10000942                                     BAR LA OFICINA
    ## 943   10000943                                TAQUERIA EL CHINITO
    ## 944   10000944           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 945   10000945 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 946   10000946 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 947   10000947            ABARROTERIA EBENEZER/Despacho a cliente
    ## 948   10000948                                TAQUERIA EL CHINITO
    ## 949   10000949                              HOSPITAL LAS AMERICAS
    ## 950   10000950                                        UBIQUO LABS
    ## 951   10000951      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 952   10000952                              HOSPITAL LAS AMERICAS
    ## 953   10000953                    TAQUERIA EL CHINITO |||Faltante
    ## 954   10000954           TIENDA LA BENDICION / Despacho a cliente
    ## 955   10000955                                TAQUERIA EL CHINITO
    ## 956   10000956                  POLLO PINULITO/Despacho a cliente
    ## 957   10000957 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 958   10000958                                TAQUERIA EL CHINITO
    ## 959   10000959        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 960   10000960                    TAQUERIA EL CHINITO |||Faltante
    ## 961   10000961            EL PINCHE OBELISCO / Despacho a cliente
    ## 962   10000962                            UBIQUO LABS |||FALTANTE
    ## 963   10000963                                        UBIQUO LABS
    ## 964   10000964                                        UBIQUO LABS
    ## 965   10000965                    TAQUERIA EL CHINITO |||Faltante
    ## 966   10000966 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 967   10000967                                     BAR LA OFICINA
    ## 968   10000968                              HOSPITAL LAS AMERICAS
    ## 969   10000969                    TAQUERIA EL CHINITO |||Faltante
    ## 970   10000970                            UBIQUO LABS |||FALTANTE
    ## 971   10000971                     EL PINCHE OBELISCO |||Faltante
    ## 972   10000972 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 973   10000973                EL GALLO NEGRO / Despacho a cliente
    ## 974   10000974 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 975   10000975                                TAQUERIA EL CHINITO
    ## 976   10000976           TIENDA LA BENDICION / Despacho a cliente
    ## 977   10000977                EL GALLO NEGRO / Despacho a cliente
    ## 978   10000978                                     BAR LA OFICINA
    ## 979   10000979                          POLLO PINULITO|||FALTANTE
    ## 980   10000980                                TAQUERIA EL CHINITO
    ## 981   10000981                       EL GALLO NEGRO |||DEVOLUCION
    ## 982   10000982                                        UBIQUO LABS
    ## 983   10000983            ABARROTERIA EBENEZER/Despacho a cliente
    ## 984   10000984                                        UBIQUO LABS
    ## 985   10000985                  POLLO PINULITO/Despacho a cliente
    ## 986   10000986                          POLLO PINULITO|||FALTANTE
    ## 987   10000987 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 988   10000988                       EL GALLO NEGRO |||DEVOLUCION
    ## 989   10000989        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 990   10000990                          POLLO PINULITO|||FALTANTE
    ## 991   10000991                                TAQUERIA EL CHINITO
    ## 992   10000992            ABARROTERIA EBENEZER/Despacho a cliente
    ## 993   10000993            EL PINCHE OBELISCO / Despacho a cliente
    ## 994   10000994                          POLLO PINULITO|||FALTANTE
    ## 995   10000995      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 996   10000996                  POLLO PINULITO/Despacho a cliente
    ## 997   10000997                  POLLO PINULITO/Despacho a cliente
    ## 998   10000998                                TAQUERIA EL CHINITO
    ## 999   10000999                     EL PINCHE OBELISCO |||Faltante
    ## 1000  10001000                EL GALLO NEGRO / Despacho a cliente
    ## 1001  10001001                       EL GALLO NEGRO |||DEVOLUCION
    ## 1002  10001002           TIENDA LA BENDICION / Despacho a cliente
    ## 1003  10001003            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1004  10001004                              HOSPITAL LAS AMERICAS
    ## 1005  10001005           TIENDA LA BENDICION / Despacho a cliente
    ## 1006  10001006                            UBIQUO LABS |||FALTANTE
    ## 1007  10001007                                     BAR LA OFICINA
    ## 1008  10001008                    TAQUERIA EL CHINITO |||Faltante
    ## 1009  10001009           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1010  10001010            EL PINCHE OBELISCO / Despacho a cliente
    ## 1011  10001011           TIENDA LA BENDICION / Despacho a cliente
    ## 1012  10001012                                     BAR LA OFICINA
    ## 1013  10001013                                TAQUERIA EL CHINITO
    ## 1014  10001014            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1015  10001015                              HOSPITAL LAS AMERICAS
    ## 1016  10001016                            UBIQUO LABS |||FALTANTE
    ## 1017  10001017        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1018  10001018                     EL PINCHE OBELISCO |||Faltante
    ## 1019  10001019            EL PINCHE OBELISCO / Despacho a cliente
    ## 1020  10001020           TIENDA LA BENDICION / Despacho a cliente
    ## 1021  10001021                          POLLO PINULITO|||FALTANTE
    ## 1022  10001022                EL GALLO NEGRO / Despacho a cliente
    ## 1023  10001023            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1024  10001024           TIENDA LA BENDICION / Despacho a cliente
    ## 1025  10001025                          POLLO PINULITO|||FALTANTE
    ## 1026  10001026                                        UBIQUO LABS
    ## 1027  10001027            EL PINCHE OBELISCO / Despacho a cliente
    ## 1028  10001028                    TAQUERIA EL CHINITO |||Faltante
    ## 1029  10001029                     EL PINCHE OBELISCO |||Faltante
    ## 1030  10001030           TIENDA LA BENDICION / Despacho a cliente
    ## 1031  10001031        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1032  10001032                  POLLO PINULITO/Despacho a cliente
    ## 1033  10001033                          POLLO PINULITO|||FALTANTE
    ## 1034  10001034           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1035  10001035                            UBIQUO LABS |||FALTANTE
    ## 1036  10001036                                TAQUERIA EL CHINITO
    ## 1037  10001037        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1038  10001038        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1039  10001039            EL PINCHE OBELISCO / Despacho a cliente
    ## 1040  10001040                                        UBIQUO LABS
    ## 1041  10001041                EL GALLO NEGRO / Despacho a cliente
    ## 1042  10001042                                     BAR LA OFICINA
    ## 1043  10001043            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1044  10001044                          POLLO PINULITO|||FALTANTE
    ## 1045  10001045                EL GALLO NEGRO / Despacho a cliente
    ## 1046  10001046                    TAQUERIA EL CHINITO |||Faltante
    ## 1047  10001047                          POLLO PINULITO|||FALTANTE
    ## 1048  10001048                EL GALLO NEGRO / Despacho a cliente
    ## 1049  10001049            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1050  10001050                    TAQUERIA EL CHINITO |||Faltante
    ## 1051  10001051                          POLLO PINULITO|||FALTANTE
    ## 1052  10001052           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1053  10001053                              HOSPITAL LAS AMERICAS
    ## 1054  10001054                EL GALLO NEGRO / Despacho a cliente
    ## 1055  10001055                            UBIQUO LABS |||FALTANTE
    ## 1056  10001056                       EL GALLO NEGRO |||DEVOLUCION
    ## 1057  10001057           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1058  10001058                          POLLO PINULITO|||FALTANTE
    ## 1059  10001059        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1060  10001060           TIENDA LA BENDICION / Despacho a cliente
    ## 1061  10001061                     EL PINCHE OBELISCO |||Faltante
    ## 1062  10001062                            UBIQUO LABS |||FALTANTE
    ## 1063  10001063                       EL GALLO NEGRO |||DEVOLUCION
    ## 1064  10001064      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1065  10001065                            UBIQUO LABS |||FALTANTE
    ## 1066  10001066 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1067  10001067                                     BAR LA OFICINA
    ## 1068  10001068           TIENDA LA BENDICION / Despacho a cliente
    ## 1069  10001069            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1070  10001070                                        UBIQUO LABS
    ## 1071  10001071        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1072  10001072                  POLLO PINULITO/Despacho a cliente
    ## 1073  10001073            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1074  10001074                            UBIQUO LABS |||FALTANTE
    ## 1075  10001075           TIENDA LA BENDICION / Despacho a cliente
    ## 1076  10001076                              HOSPITAL LAS AMERICAS
    ## 1077  10001077                  POLLO PINULITO/Despacho a cliente
    ## 1078  10001078                          POLLO PINULITO|||FALTANTE
    ## 1079  10001079                                     BAR LA OFICINA
    ## 1080  10001080            EL PINCHE OBELISCO / Despacho a cliente
    ## 1081  10001081 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1082  10001082                                TAQUERIA EL CHINITO
    ## 1083  10001083                  POLLO PINULITO/Despacho a cliente
    ## 1084  10001084                                     BAR LA OFICINA
    ## 1085  10001085      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1086  10001086                                TAQUERIA EL CHINITO
    ## 1087  10001087                                        UBIQUO LABS
    ## 1088  10001088                                        UBIQUO LABS
    ## 1089  10001089                                     BAR LA OFICINA
    ## 1090  10001090                                     BAR LA OFICINA
    ## 1091  10001091            EL PINCHE OBELISCO / Despacho a cliente
    ## 1092  10001092                                        UBIQUO LABS
    ## 1093  10001093                    TAQUERIA EL CHINITO |||Faltante
    ## 1094  10001094                              HOSPITAL LAS AMERICAS
    ## 1095  10001095                                     BAR LA OFICINA
    ## 1096  10001096 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1097  10001097        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1098  10001098      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1099  10001099                            UBIQUO LABS |||FALTANTE
    ## 1100  10001100 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1101  10001101           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1102  10001102      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1103  10001103                     EL PINCHE OBELISCO |||Faltante
    ## 1104  10001104           TIENDA LA BENDICION / Despacho a cliente
    ## 1105  10001105           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1106  10001106                                TAQUERIA EL CHINITO
    ## 1107  10001107                                        UBIQUO LABS
    ## 1108  10001108                EL GALLO NEGRO / Despacho a cliente
    ## 1109  10001109            EL PINCHE OBELISCO / Despacho a cliente
    ## 1110  10001110                    TAQUERIA EL CHINITO |||Faltante
    ## 1111  10001111                          POLLO PINULITO|||FALTANTE
    ## 1112  10001112                          POLLO PINULITO|||FALTANTE
    ## 1113  10001113                                TAQUERIA EL CHINITO
    ## 1114  10001114                     EL PINCHE OBELISCO |||Faltante
    ## 1115  10001115           TIENDA LA BENDICION / Despacho a cliente
    ## 1116  10001116                          POLLO PINULITO|||FALTANTE
    ## 1117  10001117                              HOSPITAL LAS AMERICAS
    ## 1118  10001118                    TAQUERIA EL CHINITO |||Faltante
    ## 1119  10001119           TIENDA LA BENDICION / Despacho a cliente
    ## 1120  10001120                          POLLO PINULITO|||FALTANTE
    ## 1121  10001121           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1122  10001122                  POLLO PINULITO/Despacho a cliente
    ## 1123  10001123                  POLLO PINULITO/Despacho a cliente
    ## 1124  10001124                  POLLO PINULITO/Despacho a cliente
    ## 1125  10001125                                TAQUERIA EL CHINITO
    ## 1126  10001126                                        UBIQUO LABS
    ## 1127  10001127                EL GALLO NEGRO / Despacho a cliente
    ## 1128  10001128        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1129  10001129                                TAQUERIA EL CHINITO
    ## 1130  10001130                                        UBIQUO LABS
    ## 1131  10001131                       EL GALLO NEGRO |||DEVOLUCION
    ## 1132  10001132                                TAQUERIA EL CHINITO
    ## 1133  10001133                          POLLO PINULITO|||FALTANTE
    ## 1134  10001134                                TAQUERIA EL CHINITO
    ## 1135  10001135        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1136  10001136        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1137  10001137      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1138  10001138            EL PINCHE OBELISCO / Despacho a cliente
    ## 1139  10001139        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1140  10001140                              HOSPITAL LAS AMERICAS
    ## 1141  10001141                                     BAR LA OFICINA
    ## 1142  10001142                                TAQUERIA EL CHINITO
    ## 1143  10001143                                        UBIQUO LABS
    ## 1144  10001144                EL GALLO NEGRO / Despacho a cliente
    ## 1145  10001145        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1146  10001146            EL PINCHE OBELISCO / Despacho a cliente
    ## 1147  10001147 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1148  10001148                                TAQUERIA EL CHINITO
    ## 1149  10001149 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1150  10001150           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1151  10001151                    TAQUERIA EL CHINITO |||Faltante
    ## 1152  10001152      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1153  10001153                  POLLO PINULITO/Despacho a cliente
    ## 1154  10001154                            UBIQUO LABS |||FALTANTE
    ## 1155  10001155                     EL PINCHE OBELISCO |||Faltante
    ## 1156  10001156                     EL PINCHE OBELISCO |||Faltante
    ## 1157  10001157                     EL PINCHE OBELISCO |||Faltante
    ## 1158  10001158           TIENDA LA BENDICION / Despacho a cliente
    ## 1159  10001159                     EL PINCHE OBELISCO |||Faltante
    ## 1160  10001160                EL GALLO NEGRO / Despacho a cliente
    ## 1161  10001161                EL GALLO NEGRO / Despacho a cliente
    ## 1162  10001162                              HOSPITAL LAS AMERICAS
    ## 1163  10001163      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1164  10001164                    TAQUERIA EL CHINITO |||Faltante
    ## 1165  10001165            EL PINCHE OBELISCO / Despacho a cliente
    ## 1166  10001166            EL PINCHE OBELISCO / Despacho a cliente
    ## 1167  10001167      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1168  10001168            EL PINCHE OBELISCO / Despacho a cliente
    ## 1169  10001169                                     BAR LA OFICINA
    ## 1170  10001170                          POLLO PINULITO|||FALTANTE
    ## 1171  10001171                                        UBIQUO LABS
    ## 1172  10001172                                        UBIQUO LABS
    ## 1173  10001173                                        UBIQUO LABS
    ## 1174  10001174                              HOSPITAL LAS AMERICAS
    ## 1175  10001175                     EL PINCHE OBELISCO |||Faltante
    ## 1176  10001176                                     BAR LA OFICINA
    ## 1177  10001177                            UBIQUO LABS |||FALTANTE
    ## 1178  10001178                     EL PINCHE OBELISCO |||Faltante
    ## 1179  10001179 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1180  10001180                            UBIQUO LABS |||FALTANTE
    ## 1181  10001181           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1182  10001182                              HOSPITAL LAS AMERICAS
    ## 1183  10001183            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1184  10001184                  POLLO PINULITO/Despacho a cliente
    ## 1185  10001185 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1186  10001186                EL GALLO NEGRO / Despacho a cliente
    ## 1187  10001187           TIENDA LA BENDICION / Despacho a cliente
    ## 1188  10001188        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1189  10001189           TIENDA LA BENDICION / Despacho a cliente
    ## 1190  10001190                                     BAR LA OFICINA
    ## 1191  10001191        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1192  10001192                                        UBIQUO LABS
    ## 1193  10001193      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1194  10001194            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1195  10001195 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1196  10001196                                TAQUERIA EL CHINITO
    ## 1197  10001197           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1198  10001198           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1199  10001199                    TAQUERIA EL CHINITO |||Faltante
    ## 1200  10001200                              HOSPITAL LAS AMERICAS
    ## 1201  10001201                            UBIQUO LABS |||FALTANTE
    ## 1202  10001202 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1203  10001203                                TAQUERIA EL CHINITO
    ## 1204  10001204            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1205  10001205                            UBIQUO LABS |||FALTANTE
    ## 1206  10001206                     EL PINCHE OBELISCO |||Faltante
    ## 1207  10001207            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1208  10001208                  POLLO PINULITO/Despacho a cliente
    ## 1209  10001209                    TAQUERIA EL CHINITO |||Faltante
    ## 1210  10001210                EL GALLO NEGRO / Despacho a cliente
    ## 1211  10001211            EL PINCHE OBELISCO / Despacho a cliente
    ## 1212  10001212                              HOSPITAL LAS AMERICAS
    ## 1213  10001213                                TAQUERIA EL CHINITO
    ## 1214  10001214                          POLLO PINULITO|||FALTANTE
    ## 1215  10001215 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1216  10001216            EL PINCHE OBELISCO / Despacho a cliente
    ## 1217  10001217           TIENDA LA BENDICION / Despacho a cliente
    ## 1218  10001218                  POLLO PINULITO/Despacho a cliente
    ## 1219  10001219                    TAQUERIA EL CHINITO |||Faltante
    ## 1220  10001220                       EL GALLO NEGRO |||DEVOLUCION
    ## 1221  10001221                          POLLO PINULITO|||FALTANTE
    ## 1222  10001222                                     BAR LA OFICINA
    ## 1223  10001223                            UBIQUO LABS |||FALTANTE
    ## 1224  10001224                              HOSPITAL LAS AMERICAS
    ## 1225  10001225           TIENDA LA BENDICION / Despacho a cliente
    ## 1226  10001226        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1227  10001227                     EL PINCHE OBELISCO |||Faltante
    ## 1228  10001228      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1229  10001229           TIENDA LA BENDICION / Despacho a cliente
    ## 1230  10001230            EL PINCHE OBELISCO / Despacho a cliente
    ## 1231  10001231                    TAQUERIA EL CHINITO |||Faltante
    ## 1232  10001232      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1233  10001233        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1234  10001234           TIENDA LA BENDICION / Despacho a cliente
    ## 1235  10001235                  POLLO PINULITO/Despacho a cliente
    ## 1236  10001236                            UBIQUO LABS |||FALTANTE
    ## 1237  10001237                                TAQUERIA EL CHINITO
    ## 1238  10001238                       EL GALLO NEGRO |||DEVOLUCION
    ## 1239  10001239                  POLLO PINULITO/Despacho a cliente
    ## 1240  10001240                EL GALLO NEGRO / Despacho a cliente
    ## 1241  10001241                                        UBIQUO LABS
    ## 1242  10001242                          POLLO PINULITO|||FALTANTE
    ## 1243  10001243            EL PINCHE OBELISCO / Despacho a cliente
    ## 1244  10001244 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1245  10001245           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1246  10001246                    TAQUERIA EL CHINITO |||Faltante
    ## 1247  10001247                          POLLO PINULITO|||FALTANTE
    ## 1248  10001248                EL GALLO NEGRO / Despacho a cliente
    ## 1249  10001249            EL PINCHE OBELISCO / Despacho a cliente
    ## 1250  10001250                            UBIQUO LABS |||FALTANTE
    ## 1251  10001251                     EL PINCHE OBELISCO |||Faltante
    ## 1252  10001252            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1253  10001253                                     BAR LA OFICINA
    ## 1254  10001254                       EL GALLO NEGRO |||DEVOLUCION
    ## 1255  10001255 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1256  10001256                       EL GALLO NEGRO |||DEVOLUCION
    ## 1257  10001257           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1258  10001258                              HOSPITAL LAS AMERICAS
    ## 1259  10001259                          POLLO PINULITO|||FALTANTE
    ## 1260  10001260           TIENDA LA BENDICION / Despacho a cliente
    ## 1261  10001261                                TAQUERIA EL CHINITO
    ## 1262  10001262                                     BAR LA OFICINA
    ## 1263  10001263                       EL GALLO NEGRO |||DEVOLUCION
    ## 1264  10001264                  POLLO PINULITO/Despacho a cliente
    ## 1265  10001265        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1266  10001266           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1267  10001267                                     BAR LA OFICINA
    ## 1268  10001268                            UBIQUO LABS |||FALTANTE
    ## 1269  10001269                EL GALLO NEGRO / Despacho a cliente
    ## 1270  10001270            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1271  10001271                            UBIQUO LABS |||FALTANTE
    ## 1272  10001272                            UBIQUO LABS |||FALTANTE
    ## 1273  10001273        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1274  10001274                     EL PINCHE OBELISCO |||Faltante
    ## 1275  10001275        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1276  10001276                            UBIQUO LABS |||FALTANTE
    ## 1277  10001277                       EL GALLO NEGRO |||DEVOLUCION
    ## 1278  10001278                     EL PINCHE OBELISCO |||Faltante
    ## 1279  10001279                  POLLO PINULITO/Despacho a cliente
    ## 1280  10001280                       EL GALLO NEGRO |||DEVOLUCION
    ## 1281  10001281                    TAQUERIA EL CHINITO |||Faltante
    ## 1282  10001282                                        UBIQUO LABS
    ## 1283  10001283                                TAQUERIA EL CHINITO
    ## 1284  10001284            EL PINCHE OBELISCO / Despacho a cliente
    ## 1285  10001285 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1286  10001286                EL GALLO NEGRO / Despacho a cliente
    ## 1287  10001287        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1288  10001288 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1289  10001289                              HOSPITAL LAS AMERICAS
    ## 1290  10001290            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1291  10001291                                TAQUERIA EL CHINITO
    ## 1292  10001292                              HOSPITAL LAS AMERICAS
    ## 1293  10001293                            UBIQUO LABS |||FALTANTE
    ## 1294  10001294                  POLLO PINULITO/Despacho a cliente
    ## 1295  10001295      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1296  10001296                       EL GALLO NEGRO |||DEVOLUCION
    ## 1297  10001297            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1298  10001298            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1299  10001299 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1300  10001300                          POLLO PINULITO|||FALTANTE
    ## 1301  10001301                          POLLO PINULITO|||FALTANTE
    ## 1302  10001302                                TAQUERIA EL CHINITO
    ## 1303  10001303           TIENDA LA BENDICION / Despacho a cliente
    ## 1304  10001304                     EL PINCHE OBELISCO |||Faltante
    ## 1305  10001305                       EL GALLO NEGRO |||DEVOLUCION
    ## 1306  10001306                  POLLO PINULITO/Despacho a cliente
    ## 1307  10001307                                        UBIQUO LABS
    ## 1308  10001308                  POLLO PINULITO/Despacho a cliente
    ## 1309  10001309           TIENDA LA BENDICION / Despacho a cliente
    ## 1310  10001310      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1311  10001311           TIENDA LA BENDICION / Despacho a cliente
    ## 1312  10001312            EL PINCHE OBELISCO / Despacho a cliente
    ## 1313  10001313                EL GALLO NEGRO / Despacho a cliente
    ## 1314  10001314            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1315  10001315                       EL GALLO NEGRO |||DEVOLUCION
    ## 1316  10001316                  POLLO PINULITO/Despacho a cliente
    ## 1317  10001317                              HOSPITAL LAS AMERICAS
    ## 1318  10001318           TIENDA LA BENDICION / Despacho a cliente
    ## 1319  10001319                       EL GALLO NEGRO |||DEVOLUCION
    ## 1320  10001320                     EL PINCHE OBELISCO |||Faltante
    ## 1321  10001321            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1322  10001322                       EL GALLO NEGRO |||DEVOLUCION
    ## 1323  10001323        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1324  10001324                                        UBIQUO LABS
    ## 1325  10001325           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1326  10001326                            UBIQUO LABS |||FALTANTE
    ## 1327  10001327                                     BAR LA OFICINA
    ## 1328  10001328                    TAQUERIA EL CHINITO |||Faltante
    ## 1329  10001329                  POLLO PINULITO/Despacho a cliente
    ## 1330  10001330                       EL GALLO NEGRO |||DEVOLUCION
    ## 1331  10001331 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1332  10001332                                     BAR LA OFICINA
    ## 1333  10001333           TIENDA LA BENDICION / Despacho a cliente
    ## 1334  10001334            EL PINCHE OBELISCO / Despacho a cliente
    ## 1335  10001335                                        UBIQUO LABS
    ## 1336  10001336                EL GALLO NEGRO / Despacho a cliente
    ## 1337  10001337                                TAQUERIA EL CHINITO
    ## 1338  10001338           TIENDA LA BENDICION / Despacho a cliente
    ## 1339  10001339                          POLLO PINULITO|||FALTANTE
    ## 1340  10001340                       EL GALLO NEGRO |||DEVOLUCION
    ## 1341  10001341           TIENDA LA BENDICION / Despacho a cliente
    ## 1342  10001342                     EL PINCHE OBELISCO |||Faltante
    ## 1343  10001343                  POLLO PINULITO/Despacho a cliente
    ## 1344  10001344                       EL GALLO NEGRO |||DEVOLUCION
    ## 1345  10001345                            UBIQUO LABS |||FALTANTE
    ## 1346  10001346                                     BAR LA OFICINA
    ## 1347  10001347           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1348  10001348        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1349  10001349                EL GALLO NEGRO / Despacho a cliente
    ## 1350  10001350      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1351  10001351                                     BAR LA OFICINA
    ## 1352  10001352                    TAQUERIA EL CHINITO |||Faltante
    ## 1353  10001353      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1354  10001354      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1355  10001355                  POLLO PINULITO/Despacho a cliente
    ## 1356  10001356                     EL PINCHE OBELISCO |||Faltante
    ## 1357  10001357                                     BAR LA OFICINA
    ## 1358  10001358                       EL GALLO NEGRO |||DEVOLUCION
    ## 1359  10001359                              HOSPITAL LAS AMERICAS
    ## 1360  10001360                     EL PINCHE OBELISCO |||Faltante
    ## 1361  10001361                    TAQUERIA EL CHINITO |||Faltante
    ## 1362  10001362                     EL PINCHE OBELISCO |||Faltante
    ## 1363  10001363      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1364  10001364 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1365  10001365 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1366  10001366                     EL PINCHE OBELISCO |||Faltante
    ## 1367  10001367            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1368  10001368                  POLLO PINULITO/Despacho a cliente
    ## 1369  10001369                    TAQUERIA EL CHINITO |||Faltante
    ## 1370  10001370                       EL GALLO NEGRO |||DEVOLUCION
    ## 1371  10001371                EL GALLO NEGRO / Despacho a cliente
    ## 1372  10001372           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1373  10001373 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1374  10001374            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1375  10001375            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1376  10001376                    TAQUERIA EL CHINITO |||Faltante
    ## 1377  10001377                       EL GALLO NEGRO |||DEVOLUCION
    ## 1378  10001378                                     BAR LA OFICINA
    ## 1379  10001379                          POLLO PINULITO|||FALTANTE
    ## 1380  10001380            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1381  10001381                     EL PINCHE OBELISCO |||Faltante
    ## 1382  10001382        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1383  10001383                                        UBIQUO LABS
    ## 1384  10001384                            UBIQUO LABS |||FALTANTE
    ## 1385  10001385                                     BAR LA OFICINA
    ## 1386  10001386                                        UBIQUO LABS
    ## 1387  10001387            EL PINCHE OBELISCO / Despacho a cliente
    ## 1388  10001388 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1389  10001389                                TAQUERIA EL CHINITO
    ## 1390  10001390           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1391  10001391           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1392  10001392           TIENDA LA BENDICION / Despacho a cliente
    ## 1393  10001393                    TAQUERIA EL CHINITO |||Faltante
    ## 1394  10001394                       EL GALLO NEGRO |||DEVOLUCION
    ## 1395  10001395                          POLLO PINULITO|||FALTANTE
    ## 1396  10001396      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1397  10001397                EL GALLO NEGRO / Despacho a cliente
    ## 1398  10001398           TIENDA LA BENDICION / Despacho a cliente
    ## 1399  10001399        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1400  10001400                            UBIQUO LABS |||FALTANTE
    ## 1401  10001401 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1402  10001402           TIENDA LA BENDICION / Despacho a cliente
    ## 1403  10001403                  POLLO PINULITO/Despacho a cliente
    ## 1404  10001404                                     BAR LA OFICINA
    ## 1405  10001405                                TAQUERIA EL CHINITO
    ## 1406  10001406                  POLLO PINULITO/Despacho a cliente
    ## 1407  10001407                              HOSPITAL LAS AMERICAS
    ## 1408  10001408                EL GALLO NEGRO / Despacho a cliente
    ## 1409  10001409           TIENDA LA BENDICION / Despacho a cliente
    ## 1410  10001410                                        UBIQUO LABS
    ## 1411  10001411      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1412  10001412                  POLLO PINULITO/Despacho a cliente
    ## 1413  10001413                     EL PINCHE OBELISCO |||Faltante
    ## 1414  10001414                    TAQUERIA EL CHINITO |||Faltante
    ## 1415  10001415      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1416  10001416                EL GALLO NEGRO / Despacho a cliente
    ## 1417  10001417           TIENDA LA BENDICION / Despacho a cliente
    ## 1418  10001418                       EL GALLO NEGRO |||DEVOLUCION
    ## 1419  10001419        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1420  10001420                                        UBIQUO LABS
    ## 1421  10001421                          POLLO PINULITO|||FALTANTE
    ## 1422  10001422           TIENDA LA BENDICION / Despacho a cliente
    ## 1423  10001423                          POLLO PINULITO|||FALTANTE
    ## 1424  10001424                          POLLO PINULITO|||FALTANTE
    ## 1425  10001425           TIENDA LA BENDICION / Despacho a cliente
    ## 1426  10001426                          POLLO PINULITO|||FALTANTE
    ## 1427  10001427            EL PINCHE OBELISCO / Despacho a cliente
    ## 1428  10001428                                     BAR LA OFICINA
    ## 1429  10001429                  POLLO PINULITO/Despacho a cliente
    ## 1430  10001430                                     BAR LA OFICINA
    ## 1431  10001431                       EL GALLO NEGRO |||DEVOLUCION
    ## 1432  10001432                          POLLO PINULITO|||FALTANTE
    ## 1433  10001433                            UBIQUO LABS |||FALTANTE
    ## 1434  10001434                  POLLO PINULITO/Despacho a cliente
    ## 1435  10001435                  POLLO PINULITO/Despacho a cliente
    ## 1436  10001436                                TAQUERIA EL CHINITO
    ## 1437  10001437      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1438  10001438                          POLLO PINULITO|||FALTANTE
    ## 1439  10001439                  POLLO PINULITO/Despacho a cliente
    ## 1440  10001440                          POLLO PINULITO|||FALTANTE
    ## 1441  10001441                            UBIQUO LABS |||FALTANTE
    ## 1442  10001442                  POLLO PINULITO/Despacho a cliente
    ## 1443  10001443           TIENDA LA BENDICION / Despacho a cliente
    ## 1444  10001444 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1445  10001445                EL GALLO NEGRO / Despacho a cliente
    ## 1446  10001446                            UBIQUO LABS |||FALTANTE
    ## 1447  10001447           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1448  10001448        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1449  10001449            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1450  10001450            EL PINCHE OBELISCO / Despacho a cliente
    ## 1451  10001451                                        UBIQUO LABS
    ## 1452  10001452 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1453  10001453                    TAQUERIA EL CHINITO |||Faltante
    ## 1454  10001454                              HOSPITAL LAS AMERICAS
    ## 1455  10001455                                     BAR LA OFICINA
    ## 1456  10001456                          POLLO PINULITO|||FALTANTE
    ## 1457  10001457           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1458  10001458                            UBIQUO LABS |||FALTANTE
    ## 1459  10001459      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1460  10001460            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1461  10001461                EL GALLO NEGRO / Despacho a cliente
    ## 1462  10001462 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1463  10001463           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1464  10001464                              HOSPITAL LAS AMERICAS
    ## 1465  10001465                EL GALLO NEGRO / Despacho a cliente
    ## 1466  10001466                          POLLO PINULITO|||FALTANTE
    ## 1467  10001467                                        UBIQUO LABS
    ## 1468  10001468            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1469  10001469                    TAQUERIA EL CHINITO |||Faltante
    ## 1470  10001470                            UBIQUO LABS |||FALTANTE
    ## 1471  10001471 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1472  10001472 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1473  10001473                     EL PINCHE OBELISCO |||Faltante
    ## 1474  10001474                       EL GALLO NEGRO |||DEVOLUCION
    ## 1475  10001475                              HOSPITAL LAS AMERICAS
    ## 1476  10001476            EL PINCHE OBELISCO / Despacho a cliente
    ## 1477  10001477                          POLLO PINULITO|||FALTANTE
    ## 1478  10001478                     EL PINCHE OBELISCO |||Faltante
    ## 1479  10001479                EL GALLO NEGRO / Despacho a cliente
    ## 1480  10001480           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1481  10001481            EL PINCHE OBELISCO / Despacho a cliente
    ## 1482  10001482            EL PINCHE OBELISCO / Despacho a cliente
    ## 1483  10001483                     EL PINCHE OBELISCO |||Faltante
    ## 1484  10001484                     EL PINCHE OBELISCO |||Faltante
    ## 1485  10001485            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1486  10001486      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1487  10001487           TIENDA LA BENDICION / Despacho a cliente
    ## 1488  10001488                EL GALLO NEGRO / Despacho a cliente
    ## 1489  10001489                                     BAR LA OFICINA
    ## 1490  10001490                                        UBIQUO LABS
    ## 1491  10001491                    TAQUERIA EL CHINITO |||Faltante
    ## 1492  10001492                EL GALLO NEGRO / Despacho a cliente
    ## 1493  10001493                  POLLO PINULITO/Despacho a cliente
    ## 1494  10001494                       EL GALLO NEGRO |||DEVOLUCION
    ## 1495  10001495                     EL PINCHE OBELISCO |||Faltante
    ## 1496  10001496           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1497  10001497      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1498  10001498                                        UBIQUO LABS
    ## 1499  10001499                  POLLO PINULITO/Despacho a cliente
    ## 1500  10001500                     EL PINCHE OBELISCO |||Faltante
    ## 1501  10001501                              HOSPITAL LAS AMERICAS
    ## 1502  10001502        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1503  10001503        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1504  10001504        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1505  10001505        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1506  10001506                EL GALLO NEGRO / Despacho a cliente
    ## 1507  10001507      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1508  10001508           TIENDA LA BENDICION / Despacho a cliente
    ## 1509  10001509        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1510  10001510      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1511  10001511            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1512  10001512            EL PINCHE OBELISCO / Despacho a cliente
    ## 1513  10001513           TIENDA LA BENDICION / Despacho a cliente
    ## 1514  10001514                                     BAR LA OFICINA
    ## 1515  10001515      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1516  10001516            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1517  10001517                                TAQUERIA EL CHINITO
    ## 1518  10001518                EL GALLO NEGRO / Despacho a cliente
    ## 1519  10001519                                        UBIQUO LABS
    ## 1520  10001520                                        UBIQUO LABS
    ## 1521  10001521      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1522  10001522                              HOSPITAL LAS AMERICAS
    ## 1523  10001523                          POLLO PINULITO|||FALTANTE
    ## 1524  10001524                            UBIQUO LABS |||FALTANTE
    ## 1525  10001525                       EL GALLO NEGRO |||DEVOLUCION
    ## 1526  10001526           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1527  10001527                          POLLO PINULITO|||FALTANTE
    ## 1528  10001528            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1529  10001529            EL PINCHE OBELISCO / Despacho a cliente
    ## 1530  10001530                          POLLO PINULITO|||FALTANTE
    ## 1531  10001531      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1532  10001532                                     BAR LA OFICINA
    ## 1533  10001533            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1534  10001534                  POLLO PINULITO/Despacho a cliente
    ## 1535  10001535            EL PINCHE OBELISCO / Despacho a cliente
    ## 1536  10001536                            UBIQUO LABS |||FALTANTE
    ## 1537  10001537           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1538  10001538           TIENDA LA BENDICION / Despacho a cliente
    ## 1539  10001539           TIENDA LA BENDICION / Despacho a cliente
    ## 1540  10001540                EL GALLO NEGRO / Despacho a cliente
    ## 1541  10001541            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1542  10001542                  POLLO PINULITO/Despacho a cliente
    ## 1543  10001543      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1544  10001544                                        UBIQUO LABS
    ## 1545  10001545                                        UBIQUO LABS
    ## 1546  10001546            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1547  10001547                                TAQUERIA EL CHINITO
    ## 1548  10001548                              HOSPITAL LAS AMERICAS
    ## 1549  10001549            EL PINCHE OBELISCO / Despacho a cliente
    ## 1550  10001550                          POLLO PINULITO|||FALTANTE
    ## 1551  10001551                                     BAR LA OFICINA
    ## 1552  10001552           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1553  10001553                    TAQUERIA EL CHINITO |||Faltante
    ## 1554  10001554                     EL PINCHE OBELISCO |||Faltante
    ## 1555  10001555 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1556  10001556            EL PINCHE OBELISCO / Despacho a cliente
    ## 1557  10001557           TIENDA LA BENDICION / Despacho a cliente
    ## 1558  10001558            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1559  10001559        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1560  10001560                                TAQUERIA EL CHINITO
    ## 1561  10001561                            UBIQUO LABS |||FALTANTE
    ## 1562  10001562 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1563  10001563                    TAQUERIA EL CHINITO |||Faltante
    ## 1564  10001564            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1565  10001565                                        UBIQUO LABS
    ## 1566  10001566 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1567  10001567                EL GALLO NEGRO / Despacho a cliente
    ## 1568  10001568                  POLLO PINULITO/Despacho a cliente
    ## 1569  10001569                                        UBIQUO LABS
    ## 1570  10001570                       EL GALLO NEGRO |||DEVOLUCION
    ## 1571  10001571      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1572  10001572                                        UBIQUO LABS
    ## 1573  10001573           TIENDA LA BENDICION / Despacho a cliente
    ## 1574  10001574                                        UBIQUO LABS
    ## 1575  10001575                    TAQUERIA EL CHINITO |||Faltante
    ## 1576  10001576                            UBIQUO LABS |||FALTANTE
    ## 1577  10001577                       EL GALLO NEGRO |||DEVOLUCION
    ## 1578  10001578                  POLLO PINULITO/Despacho a cliente
    ## 1579  10001579                            UBIQUO LABS |||FALTANTE
    ## 1580  10001580            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1581  10001581                EL GALLO NEGRO / Despacho a cliente
    ## 1582  10001582           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1583  10001583                            UBIQUO LABS |||FALTANTE
    ## 1584  10001584                  POLLO PINULITO/Despacho a cliente
    ## 1585  10001585                                     BAR LA OFICINA
    ## 1586  10001586      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1587  10001587                     EL PINCHE OBELISCO |||Faltante
    ## 1588  10001588                          POLLO PINULITO|||FALTANTE
    ## 1589  10001589           TIENDA LA BENDICION / Despacho a cliente
    ## 1590  10001590                     EL PINCHE OBELISCO |||Faltante
    ## 1591  10001591                  POLLO PINULITO/Despacho a cliente
    ## 1592  10001592            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1593  10001593           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1594  10001594                EL GALLO NEGRO / Despacho a cliente
    ## 1595  10001595                       EL GALLO NEGRO |||DEVOLUCION
    ## 1596  10001596                                     BAR LA OFICINA
    ## 1597  10001597                EL GALLO NEGRO / Despacho a cliente
    ## 1598  10001598                              HOSPITAL LAS AMERICAS
    ## 1599  10001599                  POLLO PINULITO/Despacho a cliente
    ## 1600  10001600            EL PINCHE OBELISCO / Despacho a cliente
    ## 1601  10001601                  POLLO PINULITO/Despacho a cliente
    ## 1602  10001602                    TAQUERIA EL CHINITO |||Faltante
    ## 1603  10001603                       EL GALLO NEGRO |||DEVOLUCION
    ## 1604  10001604                                TAQUERIA EL CHINITO
    ## 1605  10001605                       EL GALLO NEGRO |||DEVOLUCION
    ## 1606  10001606 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1607  10001607                     EL PINCHE OBELISCO |||Faltante
    ## 1608  10001608                EL GALLO NEGRO / Despacho a cliente
    ## 1609  10001609                                     BAR LA OFICINA
    ## 1610  10001610            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1611  10001611            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1612  10001612                          POLLO PINULITO|||FALTANTE
    ## 1613  10001613                  POLLO PINULITO/Despacho a cliente
    ## 1614  10001614                                     BAR LA OFICINA
    ## 1615  10001615      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1616  10001616                                        UBIQUO LABS
    ## 1617  10001617                     EL PINCHE OBELISCO |||Faltante
    ## 1618  10001618                            UBIQUO LABS |||FALTANTE
    ## 1619  10001619                              HOSPITAL LAS AMERICAS
    ## 1620  10001620                     EL PINCHE OBELISCO |||Faltante
    ## 1621  10001621        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1622  10001622                                        UBIQUO LABS
    ## 1623  10001623                       EL GALLO NEGRO |||DEVOLUCION
    ## 1624  10001624                     EL PINCHE OBELISCO |||Faltante
    ## 1625  10001625           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1626  10001626                     EL PINCHE OBELISCO |||Faltante
    ## 1627  10001627                  POLLO PINULITO/Despacho a cliente
    ## 1628  10001628           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1629  10001629                          POLLO PINULITO|||FALTANTE
    ## 1630  10001630                            UBIQUO LABS |||FALTANTE
    ## 1631  10001631                     EL PINCHE OBELISCO |||Faltante
    ## 1632  10001632                            UBIQUO LABS |||FALTANTE
    ## 1633  10001633                              HOSPITAL LAS AMERICAS
    ## 1634  10001634                                        UBIQUO LABS
    ## 1635  10001635                  POLLO PINULITO/Despacho a cliente
    ## 1636  10001636      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1637  10001637                                TAQUERIA EL CHINITO
    ## 1638  10001638           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1639  10001639                          POLLO PINULITO|||FALTANTE
    ## 1640  10001640                                        UBIQUO LABS
    ## 1641  10001641        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1642  10001642        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1643  10001643                            UBIQUO LABS |||FALTANTE
    ## 1644  10001644                    TAQUERIA EL CHINITO |||Faltante
    ## 1645  10001645                     EL PINCHE OBELISCO |||Faltante
    ## 1646  10001646                EL GALLO NEGRO / Despacho a cliente
    ## 1647  10001647                  POLLO PINULITO/Despacho a cliente
    ## 1648  10001648           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1649  10001649                          POLLO PINULITO|||FALTANTE
    ## 1650  10001650 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1651  10001651                                     BAR LA OFICINA
    ## 1652  10001652           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1653  10001653                EL GALLO NEGRO / Despacho a cliente
    ## 1654  10001654 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1655  10001655            EL PINCHE OBELISCO / Despacho a cliente
    ## 1656  10001656                     EL PINCHE OBELISCO |||Faltante
    ## 1657  10001657 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1658  10001658           TIENDA LA BENDICION / Despacho a cliente
    ## 1659  10001659                              HOSPITAL LAS AMERICAS
    ## 1660  10001660           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1661  10001661                                        UBIQUO LABS
    ## 1662  10001662                       EL GALLO NEGRO |||DEVOLUCION
    ## 1663  10001663            EL PINCHE OBELISCO / Despacho a cliente
    ## 1664  10001664                       EL GALLO NEGRO |||DEVOLUCION
    ## 1665  10001665                            UBIQUO LABS |||FALTANTE
    ## 1666  10001666                          POLLO PINULITO|||FALTANTE
    ## 1667  10001667        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1668  10001668                          POLLO PINULITO|||FALTANTE
    ## 1669  10001669                              HOSPITAL LAS AMERICAS
    ## 1670  10001670                    TAQUERIA EL CHINITO |||Faltante
    ## 1671  10001671        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1672  10001672      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1673  10001673           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1674  10001674        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1675  10001675           TIENDA LA BENDICION / Despacho a cliente
    ## 1676  10001676                  POLLO PINULITO/Despacho a cliente
    ## 1677  10001677                                TAQUERIA EL CHINITO
    ## 1678  10001678                          POLLO PINULITO|||FALTANTE
    ## 1679  10001679           TIENDA LA BENDICION / Despacho a cliente
    ## 1680  10001680                  POLLO PINULITO/Despacho a cliente
    ## 1681  10001681           TIENDA LA BENDICION / Despacho a cliente
    ## 1682  10001682                     EL PINCHE OBELISCO |||Faltante
    ## 1683  10001683        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1684  10001684           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1685  10001685           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1686  10001686            EL PINCHE OBELISCO / Despacho a cliente
    ## 1687  10001687           TIENDA LA BENDICION / Despacho a cliente
    ## 1688  10001688                                TAQUERIA EL CHINITO
    ## 1689  10001689                                TAQUERIA EL CHINITO
    ## 1690  10001690           TIENDA LA BENDICION / Despacho a cliente
    ## 1691  10001691                            UBIQUO LABS |||FALTANTE
    ## 1692  10001692        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1693  10001693            EL PINCHE OBELISCO / Despacho a cliente
    ## 1694  10001694                       EL GALLO NEGRO |||DEVOLUCION
    ## 1695  10001695                       EL GALLO NEGRO |||DEVOLUCION
    ## 1696  10001696                                        UBIQUO LABS
    ## 1697  10001697                                     BAR LA OFICINA
    ## 1698  10001698                  POLLO PINULITO/Despacho a cliente
    ## 1699  10001699                                     BAR LA OFICINA
    ## 1700  10001700                                     BAR LA OFICINA
    ## 1701  10001701           TIENDA LA BENDICION / Despacho a cliente
    ## 1702  10001702                                        UBIQUO LABS
    ## 1703  10001703                                TAQUERIA EL CHINITO
    ## 1704  10001704                EL GALLO NEGRO / Despacho a cliente
    ## 1705  10001705                     EL PINCHE OBELISCO |||Faltante
    ## 1706  10001706                                     BAR LA OFICINA
    ## 1707  10001707            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1708  10001708      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1709  10001709                              HOSPITAL LAS AMERICAS
    ## 1710  10001710                          POLLO PINULITO|||FALTANTE
    ## 1711  10001711                              HOSPITAL LAS AMERICAS
    ## 1712  10001712                          POLLO PINULITO|||FALTANTE
    ## 1713  10001713 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1714  10001714                          POLLO PINULITO|||FALTANTE
    ## 1715  10001715                                        UBIQUO LABS
    ## 1716  10001716                                TAQUERIA EL CHINITO
    ## 1717  10001717        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1718  10001718            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1719  10001719                                        UBIQUO LABS
    ## 1720  10001720           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1721  10001721 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1722  10001722                              HOSPITAL LAS AMERICAS
    ## 1723  10001723                     EL PINCHE OBELISCO |||Faltante
    ## 1724  10001724                                        UBIQUO LABS
    ## 1725  10001725                EL GALLO NEGRO / Despacho a cliente
    ## 1726  10001726           TIENDA LA BENDICION / Despacho a cliente
    ## 1727  10001727                    TAQUERIA EL CHINITO |||Faltante
    ## 1728  10001728                                TAQUERIA EL CHINITO
    ## 1729  10001729      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1730  10001730                       EL GALLO NEGRO |||DEVOLUCION
    ## 1731  10001731           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1732  10001732            EL PINCHE OBELISCO / Despacho a cliente
    ## 1733  10001733           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1734  10001734                          POLLO PINULITO|||FALTANTE
    ## 1735  10001735                EL GALLO NEGRO / Despacho a cliente
    ## 1736  10001736                          POLLO PINULITO|||FALTANTE
    ## 1737  10001737                          POLLO PINULITO|||FALTANTE
    ## 1738  10001738           TIENDA LA BENDICION / Despacho a cliente
    ## 1739  10001739        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1740  10001740        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1741  10001741                                     BAR LA OFICINA
    ## 1742  10001742            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1743  10001743      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1744  10001744        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1745  10001745        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1746  10001746                                TAQUERIA EL CHINITO
    ## 1747  10001747            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1748  10001748                          POLLO PINULITO|||FALTANTE
    ## 1749  10001749           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1750  10001750                     EL PINCHE OBELISCO |||Faltante
    ## 1751  10001751                            UBIQUO LABS |||FALTANTE
    ## 1752  10001752                          POLLO PINULITO|||FALTANTE
    ## 1753  10001753        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1754  10001754                     EL PINCHE OBELISCO |||Faltante
    ## 1755  10001755                     EL PINCHE OBELISCO |||Faltante
    ## 1756  10001756                       EL GALLO NEGRO |||DEVOLUCION
    ## 1757  10001757                                TAQUERIA EL CHINITO
    ## 1758  10001758            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1759  10001759      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1760  10001760 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1761  10001761                          POLLO PINULITO|||FALTANTE
    ## 1762  10001762                              HOSPITAL LAS AMERICAS
    ## 1763  10001763           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1764  10001764                                        UBIQUO LABS
    ## 1765  10001765                            UBIQUO LABS |||FALTANTE
    ## 1766  10001766        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1767  10001767 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1768  10001768           TIENDA LA BENDICION / Despacho a cliente
    ## 1769  10001769      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1770  10001770                              HOSPITAL LAS AMERICAS
    ## 1771  10001771                                TAQUERIA EL CHINITO
    ## 1772  10001772 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1773  10001773 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1774  10001774                          POLLO PINULITO|||FALTANTE
    ## 1775  10001775 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1776  10001776            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1777  10001777                  POLLO PINULITO/Despacho a cliente
    ## 1778  10001778                EL GALLO NEGRO / Despacho a cliente
    ## 1779  10001779                                TAQUERIA EL CHINITO
    ## 1780  10001780                                        UBIQUO LABS
    ## 1781  10001781                EL GALLO NEGRO / Despacho a cliente
    ## 1782  10001782                                TAQUERIA EL CHINITO
    ## 1783  10001783                                        UBIQUO LABS
    ## 1784  10001784                    TAQUERIA EL CHINITO |||Faltante
    ## 1785  10001785                       EL GALLO NEGRO |||DEVOLUCION
    ## 1786  10001786           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1787  10001787                       EL GALLO NEGRO |||DEVOLUCION
    ## 1788  10001788            EL PINCHE OBELISCO / Despacho a cliente
    ## 1789  10001789                            UBIQUO LABS |||FALTANTE
    ## 1790  10001790                          POLLO PINULITO|||FALTANTE
    ## 1791  10001791                                        UBIQUO LABS
    ## 1792  10001792                       EL GALLO NEGRO |||DEVOLUCION
    ## 1793  10001793                                TAQUERIA EL CHINITO
    ## 1794  10001794            EL PINCHE OBELISCO / Despacho a cliente
    ## 1795  10001795                              HOSPITAL LAS AMERICAS
    ## 1796  10001796                       EL GALLO NEGRO |||DEVOLUCION
    ## 1797  10001797           TIENDA LA BENDICION / Despacho a cliente
    ## 1798  10001798                    TAQUERIA EL CHINITO |||Faltante
    ## 1799  10001799 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1800  10001800        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1801  10001801            EL PINCHE OBELISCO / Despacho a cliente
    ## 1802  10001802                     EL PINCHE OBELISCO |||Faltante
    ## 1803  10001803                                TAQUERIA EL CHINITO
    ## 1804  10001804            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1805  10001805 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1806  10001806                       EL GALLO NEGRO |||DEVOLUCION
    ## 1807  10001807                            UBIQUO LABS |||FALTANTE
    ## 1808  10001808      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1809  10001809                            UBIQUO LABS |||FALTANTE
    ## 1810  10001810                    TAQUERIA EL CHINITO |||Faltante
    ## 1811  10001811            EL PINCHE OBELISCO / Despacho a cliente
    ## 1812  10001812                              HOSPITAL LAS AMERICAS
    ## 1813  10001813                    TAQUERIA EL CHINITO |||Faltante
    ## 1814  10001814            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1815  10001815           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1816  10001816            EL PINCHE OBELISCO / Despacho a cliente
    ## 1817  10001817                     EL PINCHE OBELISCO |||Faltante
    ## 1818  10001818                    TAQUERIA EL CHINITO |||Faltante
    ## 1819  10001819                     EL PINCHE OBELISCO |||Faltante
    ## 1820  10001820                                     BAR LA OFICINA
    ## 1821  10001821            EL PINCHE OBELISCO / Despacho a cliente
    ## 1822  10001822        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1823  10001823                              HOSPITAL LAS AMERICAS
    ## 1824  10001824                                     BAR LA OFICINA
    ## 1825  10001825            EL PINCHE OBELISCO / Despacho a cliente
    ## 1826  10001826      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1827  10001827                              HOSPITAL LAS AMERICAS
    ## 1828  10001828                    TAQUERIA EL CHINITO |||Faltante
    ## 1829  10001829                     EL PINCHE OBELISCO |||Faltante
    ## 1830  10001830            EL PINCHE OBELISCO / Despacho a cliente
    ## 1831  10001831        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1832  10001832                                     BAR LA OFICINA
    ## 1833  10001833                  POLLO PINULITO/Despacho a cliente
    ## 1834  10001834                  POLLO PINULITO/Despacho a cliente
    ## 1835  10001835        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1836  10001836            EL PINCHE OBELISCO / Despacho a cliente
    ## 1837  10001837                                        UBIQUO LABS
    ## 1838  10001838           TIENDA LA BENDICION / Despacho a cliente
    ## 1839  10001839                       EL GALLO NEGRO |||DEVOLUCION
    ## 1840  10001840           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1841  10001841                EL GALLO NEGRO / Despacho a cliente
    ## 1842  10001842                                        UBIQUO LABS
    ## 1843  10001843                            UBIQUO LABS |||FALTANTE
    ## 1844  10001844                                TAQUERIA EL CHINITO
    ## 1845  10001845                    TAQUERIA EL CHINITO |||Faltante
    ## 1846  10001846                            UBIQUO LABS |||FALTANTE
    ## 1847  10001847                                     BAR LA OFICINA
    ## 1848  10001848                                        UBIQUO LABS
    ## 1849  10001849                       EL GALLO NEGRO |||DEVOLUCION
    ## 1850  10001850                              HOSPITAL LAS AMERICAS
    ## 1851  10001851      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1852  10001852                            UBIQUO LABS |||FALTANTE
    ## 1853  10001853                                TAQUERIA EL CHINITO
    ## 1854  10001854           TIENDA LA BENDICION / Despacho a cliente
    ## 1855  10001855            EL PINCHE OBELISCO / Despacho a cliente
    ## 1856  10001856                                     BAR LA OFICINA
    ## 1857  10001857           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1858  10001858                       EL GALLO NEGRO |||DEVOLUCION
    ## 1859  10001859                            UBIQUO LABS |||FALTANTE
    ## 1860  10001860                                        UBIQUO LABS
    ## 1861  10001861                EL GALLO NEGRO / Despacho a cliente
    ## 1862  10001862 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1863  10001863                            UBIQUO LABS |||FALTANTE
    ## 1864  10001864                     EL PINCHE OBELISCO |||Faltante
    ## 1865  10001865                          POLLO PINULITO|||FALTANTE
    ## 1866  10001866 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1867  10001867      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1868  10001868                                     BAR LA OFICINA
    ## 1869  10001869                                        UBIQUO LABS
    ## 1870  10001870 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1871  10001871            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1872  10001872 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1873  10001873            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1874  10001874                EL GALLO NEGRO / Despacho a cliente
    ## 1875  10001875      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1876  10001876           TIENDA LA BENDICION / Despacho a cliente
    ## 1877  10001877                                TAQUERIA EL CHINITO
    ## 1878  10001878                EL GALLO NEGRO / Despacho a cliente
    ## 1879  10001879                       EL GALLO NEGRO |||DEVOLUCION
    ## 1880  10001880            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1881  10001881                            UBIQUO LABS |||FALTANTE
    ## 1882  10001882                                TAQUERIA EL CHINITO
    ## 1883  10001883                            UBIQUO LABS |||FALTANTE
    ## 1884  10001884            EL PINCHE OBELISCO / Despacho a cliente
    ## 1885  10001885                                     BAR LA OFICINA
    ## 1886  10001886                                     BAR LA OFICINA
    ## 1887  10001887                                     BAR LA OFICINA
    ## 1888  10001888                       EL GALLO NEGRO |||DEVOLUCION
    ## 1889  10001889                            UBIQUO LABS |||FALTANTE
    ## 1890  10001890                                TAQUERIA EL CHINITO
    ## 1891  10001891            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1892  10001892                     EL PINCHE OBELISCO |||Faltante
    ## 1893  10001893                            UBIQUO LABS |||FALTANTE
    ## 1894  10001894           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1895  10001895            EL PINCHE OBELISCO / Despacho a cliente
    ## 1896  10001896                          POLLO PINULITO|||FALTANTE
    ## 1897  10001897                    TAQUERIA EL CHINITO |||Faltante
    ## 1898  10001898                                TAQUERIA EL CHINITO
    ## 1899  10001899                EL GALLO NEGRO / Despacho a cliente
    ## 1900  10001900 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1901  10001901                                TAQUERIA EL CHINITO
    ## 1902  10001902                                TAQUERIA EL CHINITO
    ## 1903  10001903                                TAQUERIA EL CHINITO
    ## 1904  10001904           TIENDA LA BENDICION / Despacho a cliente
    ## 1905  10001905           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1906  10001906            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1907  10001907                              HOSPITAL LAS AMERICAS
    ## 1908  10001908                     EL PINCHE OBELISCO |||Faltante
    ## 1909  10001909      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1910  10001910            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1911  10001911                                        UBIQUO LABS
    ## 1912  10001912            EL PINCHE OBELISCO / Despacho a cliente
    ## 1913  10001913            EL PINCHE OBELISCO / Despacho a cliente
    ## 1914  10001914                                TAQUERIA EL CHINITO
    ## 1915  10001915      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1916  10001916                EL GALLO NEGRO / Despacho a cliente
    ## 1917  10001917            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1918  10001918                     EL PINCHE OBELISCO |||Faltante
    ## 1919  10001919        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1920  10001920        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1921  10001921 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1922  10001922                     EL PINCHE OBELISCO |||Faltante
    ## 1923  10001923      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1924  10001924           TIENDA LA BENDICION / Despacho a cliente
    ## 1925  10001925                     EL PINCHE OBELISCO |||Faltante
    ## 1926  10001926                          POLLO PINULITO|||FALTANTE
    ## 1927  10001927            EL PINCHE OBELISCO / Despacho a cliente
    ## 1928  10001928                                        UBIQUO LABS
    ## 1929  10001929            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1930  10001930           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1931  10001931                    TAQUERIA EL CHINITO |||Faltante
    ## 1932  10001932                                TAQUERIA EL CHINITO
    ## 1933  10001933                              HOSPITAL LAS AMERICAS
    ## 1934  10001934        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1935  10001935 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 1936  10001936                  POLLO PINULITO/Despacho a cliente
    ## 1937  10001937           TIENDA LA BENDICION / Despacho a cliente
    ## 1938  10001938                    TAQUERIA EL CHINITO |||Faltante
    ## 1939  10001939            EL PINCHE OBELISCO / Despacho a cliente
    ## 1940  10001940                  POLLO PINULITO/Despacho a cliente
    ## 1941  10001941            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1942  10001942                  POLLO PINULITO/Despacho a cliente
    ## 1943  10001943                              HOSPITAL LAS AMERICAS
    ## 1944  10001944                          POLLO PINULITO|||FALTANTE
    ## 1945  10001945            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1946  10001946                                     BAR LA OFICINA
    ## 1947  10001947           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1948  10001948                                TAQUERIA EL CHINITO
    ## 1949  10001949                                TAQUERIA EL CHINITO
    ## 1950  10001950                                     BAR LA OFICINA
    ## 1951  10001951                    TAQUERIA EL CHINITO |||Faltante
    ## 1952  10001952                                     BAR LA OFICINA
    ## 1953  10001953            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1954  10001954            EL PINCHE OBELISCO / Despacho a cliente
    ## 1955  10001955           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 1956  10001956            EL PINCHE OBELISCO / Despacho a cliente
    ## 1957  10001957                       EL GALLO NEGRO |||DEVOLUCION
    ## 1958  10001958                                TAQUERIA EL CHINITO
    ## 1959  10001959           TIENDA LA BENDICION / Despacho a cliente
    ## 1960  10001960            EL PINCHE OBELISCO / Despacho a cliente
    ## 1961  10001961                  POLLO PINULITO/Despacho a cliente
    ## 1962  10001962                              HOSPITAL LAS AMERICAS
    ## 1963  10001963           TIENDA LA BENDICION / Despacho a cliente
    ## 1964  10001964                    TAQUERIA EL CHINITO |||Faltante
    ## 1965  10001965                                TAQUERIA EL CHINITO
    ## 1966  10001966        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1967  10001967                              HOSPITAL LAS AMERICAS
    ## 1968  10001968                                TAQUERIA EL CHINITO
    ## 1969  10001969                     EL PINCHE OBELISCO |||Faltante
    ## 1970  10001970                          POLLO PINULITO|||FALTANTE
    ## 1971  10001971      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1972  10001972      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1973  10001973                  POLLO PINULITO/Despacho a cliente
    ## 1974  10001974                       EL GALLO NEGRO |||DEVOLUCION
    ## 1975  10001975            EL PINCHE OBELISCO / Despacho a cliente
    ## 1976  10001976                EL GALLO NEGRO / Despacho a cliente
    ## 1977  10001977                    TAQUERIA EL CHINITO |||Faltante
    ## 1978  10001978      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1979  10001979      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1980  10001980                EL GALLO NEGRO / Despacho a cliente
    ## 1981  10001981                     EL PINCHE OBELISCO |||Faltante
    ## 1982  10001982                            UBIQUO LABS |||FALTANTE
    ## 1983  10001983      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1984  10001984                EL GALLO NEGRO / Despacho a cliente
    ## 1985  10001985            EL PINCHE OBELISCO / Despacho a cliente
    ## 1986  10001986                       EL GALLO NEGRO |||DEVOLUCION
    ## 1987  10001987                                        UBIQUO LABS
    ## 1988  10001988      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1989  10001989                              HOSPITAL LAS AMERICAS
    ## 1990  10001990                            UBIQUO LABS |||FALTANTE
    ## 1991  10001991                                TAQUERIA EL CHINITO
    ## 1992  10001992                                     BAR LA OFICINA
    ## 1993  10001993        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 1994  10001994                       EL GALLO NEGRO |||DEVOLUCION
    ## 1995  10001995      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 1996  10001996                                     BAR LA OFICINA
    ## 1997  10001997            ABARROTERIA EBENEZER/Despacho a cliente
    ## 1998  10001998                       EL GALLO NEGRO |||DEVOLUCION
    ## 1999  10001999                                     BAR LA OFICINA
    ## 2000  10002000                    TAQUERIA EL CHINITO |||Faltante
    ## 2001  10002001 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2002  10002002                    TAQUERIA EL CHINITO |||Faltante
    ## 2003  10002003                                TAQUERIA EL CHINITO
    ## 2004  10002004                EL GALLO NEGRO / Despacho a cliente
    ## 2005  10002005            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2006  10002006        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2007  10002007 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2008  10002008            EL PINCHE OBELISCO / Despacho a cliente
    ## 2009  10002009        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2010  10002010           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2011  10002011                                     BAR LA OFICINA
    ## 2012  10002012                                TAQUERIA EL CHINITO
    ## 2013  10002013                                        UBIQUO LABS
    ## 2014  10002014                     EL PINCHE OBELISCO |||Faltante
    ## 2015  10002015                          POLLO PINULITO|||FALTANTE
    ## 2016  10002016      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2017  10002017                                        UBIQUO LABS
    ## 2018  10002018            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2019  10002019                            UBIQUO LABS |||FALTANTE
    ## 2020  10002020                EL GALLO NEGRO / Despacho a cliente
    ## 2021  10002021           TIENDA LA BENDICION / Despacho a cliente
    ## 2022  10002022 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2023  10002023            EL PINCHE OBELISCO / Despacho a cliente
    ## 2024  10002024                       EL GALLO NEGRO |||DEVOLUCION
    ## 2025  10002025                    TAQUERIA EL CHINITO |||Faltante
    ## 2026  10002026            EL PINCHE OBELISCO / Despacho a cliente
    ## 2027  10002027                     EL PINCHE OBELISCO |||Faltante
    ## 2028  10002028                          POLLO PINULITO|||FALTANTE
    ## 2029  10002029                    TAQUERIA EL CHINITO |||Faltante
    ## 2030  10002030                EL GALLO NEGRO / Despacho a cliente
    ## 2031  10002031                              HOSPITAL LAS AMERICAS
    ## 2032  10002032            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2033  10002033                                TAQUERIA EL CHINITO
    ## 2034  10002034                     EL PINCHE OBELISCO |||Faltante
    ## 2035  10002035                              HOSPITAL LAS AMERICAS
    ## 2036  10002036                    TAQUERIA EL CHINITO |||Faltante
    ## 2037  10002037                       EL GALLO NEGRO |||DEVOLUCION
    ## 2038  10002038                          POLLO PINULITO|||FALTANTE
    ## 2039  10002039            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2040  10002040                       EL GALLO NEGRO |||DEVOLUCION
    ## 2041  10002041                    TAQUERIA EL CHINITO |||Faltante
    ## 2042  10002042                EL GALLO NEGRO / Despacho a cliente
    ## 2043  10002043                    TAQUERIA EL CHINITO |||Faltante
    ## 2044  10002044                EL GALLO NEGRO / Despacho a cliente
    ## 2045  10002045                          POLLO PINULITO|||FALTANTE
    ## 2046  10002046                                        UBIQUO LABS
    ## 2047  10002047                                TAQUERIA EL CHINITO
    ## 2048  10002048           TIENDA LA BENDICION / Despacho a cliente
    ## 2049  10002049                              HOSPITAL LAS AMERICAS
    ## 2050  10002050                                        UBIQUO LABS
    ## 2051  10002051                EL GALLO NEGRO / Despacho a cliente
    ## 2052  10002052           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2053  10002053           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2054  10002054                       EL GALLO NEGRO |||DEVOLUCION
    ## 2055  10002055                              HOSPITAL LAS AMERICAS
    ## 2056  10002056        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2057  10002057                                     BAR LA OFICINA
    ## 2058  10002058                                TAQUERIA EL CHINITO
    ## 2059  10002059           TIENDA LA BENDICION / Despacho a cliente
    ## 2060  10002060                       EL GALLO NEGRO |||DEVOLUCION
    ## 2061  10002061                          POLLO PINULITO|||FALTANTE
    ## 2062  10002062                                TAQUERIA EL CHINITO
    ## 2063  10002063                                     BAR LA OFICINA
    ## 2064  10002064                     EL PINCHE OBELISCO |||Faltante
    ## 2065  10002065                       EL GALLO NEGRO |||DEVOLUCION
    ## 2066  10002066                     EL PINCHE OBELISCO |||Faltante
    ## 2067  10002067                          POLLO PINULITO|||FALTANTE
    ## 2068  10002068 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2069  10002069            EL PINCHE OBELISCO / Despacho a cliente
    ## 2070  10002070 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2071  10002071 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2072  10002072                              HOSPITAL LAS AMERICAS
    ## 2073  10002073           TIENDA LA BENDICION / Despacho a cliente
    ## 2074  10002074                          POLLO PINULITO|||FALTANTE
    ## 2075  10002075            EL PINCHE OBELISCO / Despacho a cliente
    ## 2076  10002076                          POLLO PINULITO|||FALTANTE
    ## 2077  10002077                EL GALLO NEGRO / Despacho a cliente
    ## 2078  10002078        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2079  10002079                    TAQUERIA EL CHINITO |||Faltante
    ## 2080  10002080                  POLLO PINULITO/Despacho a cliente
    ## 2081  10002081                    TAQUERIA EL CHINITO |||Faltante
    ## 2082  10002082                              HOSPITAL LAS AMERICAS
    ## 2083  10002083                            UBIQUO LABS |||FALTANTE
    ## 2084  10002084      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2085  10002085            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2086  10002086           TIENDA LA BENDICION / Despacho a cliente
    ## 2087  10002087                          POLLO PINULITO|||FALTANTE
    ## 2088  10002088                          POLLO PINULITO|||FALTANTE
    ## 2089  10002089                  POLLO PINULITO/Despacho a cliente
    ## 2090  10002090           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2091  10002091                     EL PINCHE OBELISCO |||Faltante
    ## 2092  10002092                              HOSPITAL LAS AMERICAS
    ## 2093  10002093      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2094  10002094           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2095  10002095                       EL GALLO NEGRO |||DEVOLUCION
    ## 2096  10002096                                TAQUERIA EL CHINITO
    ## 2097  10002097                  POLLO PINULITO/Despacho a cliente
    ## 2098  10002098                EL GALLO NEGRO / Despacho a cliente
    ## 2099  10002099                    TAQUERIA EL CHINITO |||Faltante
    ## 2100  10002100                              HOSPITAL LAS AMERICAS
    ## 2101  10002101                                     BAR LA OFICINA
    ## 2102  10002102                                     BAR LA OFICINA
    ## 2103  10002103                     EL PINCHE OBELISCO |||Faltante
    ## 2104  10002104            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2105  10002105                              HOSPITAL LAS AMERICAS
    ## 2106  10002106                  POLLO PINULITO/Despacho a cliente
    ## 2107  10002107           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2108  10002108           TIENDA LA BENDICION / Despacho a cliente
    ## 2109  10002109                              HOSPITAL LAS AMERICAS
    ## 2110  10002110                                TAQUERIA EL CHINITO
    ## 2111  10002111                    TAQUERIA EL CHINITO |||Faltante
    ## 2112  10002112            EL PINCHE OBELISCO / Despacho a cliente
    ## 2113  10002113                                     BAR LA OFICINA
    ## 2114  10002114            EL PINCHE OBELISCO / Despacho a cliente
    ## 2115  10002115                                     BAR LA OFICINA
    ## 2116  10002116           TIENDA LA BENDICION / Despacho a cliente
    ## 2117  10002117                       EL GALLO NEGRO |||DEVOLUCION
    ## 2118  10002118                                     BAR LA OFICINA
    ## 2119  10002119                          POLLO PINULITO|||FALTANTE
    ## 2120  10002120            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2121  10002121      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2122  10002122        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2123  10002123           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2124  10002124                EL GALLO NEGRO / Despacho a cliente
    ## 2125  10002125            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2126  10002126            EL PINCHE OBELISCO / Despacho a cliente
    ## 2127  10002127        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2128  10002128                              HOSPITAL LAS AMERICAS
    ## 2129  10002129                                TAQUERIA EL CHINITO
    ## 2130  10002130                          POLLO PINULITO|||FALTANTE
    ## 2131  10002131                     EL PINCHE OBELISCO |||Faltante
    ## 2132  10002132                            UBIQUO LABS |||FALTANTE
    ## 2133  10002133                EL GALLO NEGRO / Despacho a cliente
    ## 2134  10002134        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2135  10002135                          POLLO PINULITO|||FALTANTE
    ## 2136  10002136                EL GALLO NEGRO / Despacho a cliente
    ## 2137  10002137      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2138  10002138            EL PINCHE OBELISCO / Despacho a cliente
    ## 2139  10002139           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2140  10002140                                TAQUERIA EL CHINITO
    ## 2141  10002141        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2142  10002142            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2143  10002143 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2144  10002144            EL PINCHE OBELISCO / Despacho a cliente
    ## 2145  10002145           TIENDA LA BENDICION / Despacho a cliente
    ## 2146  10002146                EL GALLO NEGRO / Despacho a cliente
    ## 2147  10002147                                     BAR LA OFICINA
    ## 2148  10002148                       EL GALLO NEGRO |||DEVOLUCION
    ## 2149  10002149        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2150  10002150           TIENDA LA BENDICION / Despacho a cliente
    ## 2151  10002151                                        UBIQUO LABS
    ## 2152  10002152                          POLLO PINULITO|||FALTANTE
    ## 2153  10002153                                     BAR LA OFICINA
    ## 2154  10002154           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2155  10002155           HOSPITAL ROOSEVELT / Despacho a cliente 
    ## 2156  10002156                     EL PINCHE OBELISCO |||Faltante
    ## 2157  10002157                          POLLO PINULITO|||FALTANTE
    ## 2158  10002158                     EL PINCHE OBELISCO |||Faltante
    ## 2159  10002159                     EL PINCHE OBELISCO |||Faltante
    ## 2160  10002160            ABARROTERIA EBENEZER/Despacho a cliente
    ## 2161  10002161      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2162  10002162      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2163  10002163                              HOSPITAL LAS AMERICAS
    ## 2164  10002164                              HOSPITAL LAS AMERICAS
    ## 2165  10002165                                     BAR LA OFICINA
    ## 2166  10002166 UNIVERSIDAD FRANCISCO MARROQUIN/Despacho a cliente
    ## 2167  10002167                EL GALLO NEGRO / Despacho a cliente
    ## 2168  10002168            EL PINCHE OBELISCO / Despacho a cliente
    ## 2169  10002169                    TAQUERIA EL CHINITO |||Faltante
    ## 2170  10002170      CHICHARRONERIA EL RICO COLESTEROL |||Faltante
    ## 2171  10002171                                        UBIQUO LABS
    ## 2172  10002172                                     BAR LA OFICINA
    ## 2173  10002173                  POLLO PINULITO/Despacho a cliente
    ## 2174  10002174        SPORTA, S.A./Despacho a cliente |||Faltante
    ## 2175  10002175                    TAQUERIA EL CHINITO |||Faltante
    ## 2176  10002176                                     BAR LA OFICINA
    ## 2177  10002177            EL PINCHE OBELISCO / Despacho a cliente
    ## 2178  10002178                            UBIQUO LABS |||FALTANTE
    ## 2179  10002179                EL GALLO NEGRO / Despacho a cliente
    ## 2180  10002180            ABARROTERIA EBENEZER/Despacho a cliente
    ##      UBICACION CANTIDAD                        PILOTO      Q CREDITO
    ## 1        76002     1200       Fernando Mariano Berrio 300.00      30
    ## 2        76002     1433        Hector Aragones Frutos 358.25      90
    ## 3        76002     1857          Pedro Alvarez Parejo 464.25      60
    ## 4        76002      339          Angel Valdez Alegria  84.75      30
    ## 5        76001     1644 Juan Francisco Portillo Gomez 411.00      30
    ## 6        76001     1827             Luis Jaime Urbano 456.75      30
    ## 7        76002     1947      Ismael Rodero Monteagudo 486.75      90
    ## 8        76001     1716 Juan Francisco Portillo Gomez 429.00      60
    ## 9        76002     1601      Ismael Rodero Monteagudo 400.25      30
    ## 10       76002     1343       Fernando Mariano Berrio 335.75      90
    ## 11       76001     1782             Luis Jaime Urbano 445.50      60
    ## 12       76002      234              Felipe Villatoro  58.50      30
    ## 13       76001     1542        Hector Aragones Frutos 385.50      60
    ## 14       76001      304        Hector Aragones Frutos  76.00      90
    ## 15       76001     1667             Luis Jaime Urbano 416.75      90
    ## 16       76002     1325             Luis Jaime Urbano 331.25      30
    ## 17       76002     1186      Ismael Rodero Monteagudo 296.50      30
    ## 18       76002      231      Ismael Rodero Monteagudo  57.75      60
    ## 19       76002      783          Pedro Alvarez Parejo 195.75      30
    ## 20       76001      971              Felipe Villatoro 242.75      60
    ## 21       76002      547       Fernando Mariano Berrio 136.75      90
    ## 22       76001     1550       Fernando Mariano Berrio 387.50      30
    ## 23       76001      335          Pedro Alvarez Parejo  83.75      60
    ## 24       76002     1173          Pedro Alvarez Parejo 293.25      90
    ## 25       76001     1061       Fernando Mariano Berrio 265.25      60
    ## 26       76002      840 Juan Francisco Portillo Gomez 210.00      30
    ## 27       76002      795       Fernando Mariano Berrio 198.75      60
    ## 28       76002     1330          Angel Valdez Alegria 332.50      30
    ## 29       76001     1648 Juan Francisco Portillo Gomez 412.00      30
    ## 30       76002     1502                  Hector Giron 375.50      90
    ## 31       76001     1659 Juan Francisco Portillo Gomez 414.75      30
    ## 32       76002     1508                  Hector Giron 377.00      60
    ## 33       76002      875 Juan Francisco Portillo Gomez 218.75      60
    ## 34       76001      342        Hector Aragones Frutos  85.50      60
    ## 35       76001     1980          Pedro Alvarez Parejo 495.00      60
    ## 36       76002     1442              Felipe Villatoro 360.50      30
    ## 37       76001     1467        Hector Aragones Frutos 366.75      60
    ## 38       76001     1991        Hector Aragones Frutos 497.75      90
    ## 39       76001     1589        Hector Aragones Frutos 397.25      30
    ## 40       76001      732              Felipe Villatoro 183.00      30
    ## 41       76002      766              Felipe Villatoro 191.50      30
    ## 42       76002      827        Hector Aragones Frutos 206.75      90
    ## 43       76001     1027       Fernando Mariano Berrio 256.75      60
    ## 44       76001     1706             Luis Jaime Urbano 426.50      60
    ## 45       76001     1044      Ismael Rodero Monteagudo 261.00      60
    ## 46       76002      596             Luis Jaime Urbano 149.00      60
    ## 47       76002      362             Luis Jaime Urbano  90.50      90
    ## 48       76002     1937      Ismael Rodero Monteagudo 484.25      60
    ## 49       76002      297          Angel Valdez Alegria  74.25      90
    ## 50       76001      400      Ismael Rodero Monteagudo 100.00      90
    ## 51       76001      225        Hector Aragones Frutos  56.25      60
    ## 52       76002      562      Ismael Rodero Monteagudo 140.50      60
    ## 53       76001     1791       Fernando Mariano Berrio 447.75      60
    ## 54       76001      356             Luis Jaime Urbano  89.00      30
    ## 55       76002     1903             Luis Jaime Urbano 475.75      30
    ## 56       76002     1231          Pedro Alvarez Parejo 307.75      30
    ## 57       76002     1682        Hector Aragones Frutos 420.50      60
    ## 58       76001     1653          Pedro Alvarez Parejo 413.25      90
    ## 59       76001     1907          Angel Valdez Alegria 476.75      30
    ## 60       76002     1954      Ismael Rodero Monteagudo 488.50      90
    ## 61       76002     1177          Pedro Alvarez Parejo 294.25      90
    ## 62       76001     1247 Juan Francisco Portillo Gomez 311.75      90
    ## 63       76001     1551                  Hector Giron 387.75      90
    ## 64       76002     1481             Luis Jaime Urbano 370.25      30
    ## 65       76001     1126          Angel Valdez Alegria 281.50      60
    ## 66       76001     1239             Luis Jaime Urbano 309.75      30
    ## 67       76002     1598       Fernando Mariano Berrio 399.50      90
    ## 68       76002      965                  Hector Giron 241.25      90
    ## 69       76001     1111        Hector Aragones Frutos 277.75      30
    ## 70       76002     1092          Pedro Alvarez Parejo 273.00      30
    ## 71       76002     1107      Ismael Rodero Monteagudo 276.75      30
    ## 72       76002      958      Ismael Rodero Monteagudo 239.50      90
    ## 73       76002     1402              Felipe Villatoro 350.50      60
    ## 74       76001     1059 Juan Francisco Portillo Gomez 264.75      60
    ## 75       76001      592              Felipe Villatoro 148.00      30
    ## 76       76002     1278             Luis Jaime Urbano 319.50      90
    ## 77       76001     1578                  Hector Giron 394.50      90
    ## 78       76002     1760 Juan Francisco Portillo Gomez 440.00      30
    ## 79       76001      628          Angel Valdez Alegria 157.00      90
    ## 80       76002     1221          Angel Valdez Alegria 305.25      60
    ## 81       76002      547       Fernando Mariano Berrio 136.75      30
    ## 82       76001      742       Fernando Mariano Berrio 185.50      30
    ## 83       76002     1709          Pedro Alvarez Parejo 427.25      90
    ## 84       76002     1769          Pedro Alvarez Parejo 442.25      30
    ## 85       76002      384      Ismael Rodero Monteagudo  96.00      90
    ## 86       76001     1203      Ismael Rodero Monteagudo 300.75      60
    ## 87       76001      663                  Hector Giron 165.75      90
    ## 88       76001      929                  Hector Giron 232.25      90
    ## 89       76001      859        Hector Aragones Frutos 214.75      60
    ## 90       76002     1144          Pedro Alvarez Parejo 286.00      60
    ## 91       76001     1351        Hector Aragones Frutos 337.75      90
    ## 92       76002     1134 Juan Francisco Portillo Gomez 283.50      30
    ## 93       76002     1929          Pedro Alvarez Parejo 482.25      90
    ## 94       76002     1285              Felipe Villatoro 321.25      30
    ## 95       76002     1256          Angel Valdez Alegria 314.00      30
    ## 96       76001      516        Hector Aragones Frutos 129.00      30
    ## 97       76001      829          Angel Valdez Alegria 207.25      30
    ## 98       76002     1706       Fernando Mariano Berrio 426.50      90
    ## 99       76001     1201      Ismael Rodero Monteagudo 300.25      60
    ## 100      76001     1373      Ismael Rodero Monteagudo 343.25      30
    ## 101      76001     1164       Fernando Mariano Berrio 291.00      90
    ## 102      76001     1405             Luis Jaime Urbano 351.25      60
    ## 103      76002     1722          Pedro Alvarez Parejo 430.50      30
    ## 104      76001      666          Pedro Alvarez Parejo 166.50      90
    ## 105      76001      595      Ismael Rodero Monteagudo 148.75      60
    ## 106      76001      482              Felipe Villatoro 120.50      90
    ## 107      76001     1340       Fernando Mariano Berrio 335.00      90
    ## 108      76002     1887          Pedro Alvarez Parejo 471.75      60
    ## 109      76001      835                  Hector Giron 208.75      30
    ## 110      76001      696             Luis Jaime Urbano 174.00      60
    ## 111      76002      414       Fernando Mariano Berrio 103.50      60
    ## 112      76001     1888          Pedro Alvarez Parejo 472.00      30
    ## 113      76001     1080              Felipe Villatoro 270.00      30
    ## 114      76002     1070 Juan Francisco Portillo Gomez 267.50      90
    ## 115      76001      710       Fernando Mariano Berrio 177.50      60
    ## 116      76001      557              Felipe Villatoro 139.25      90
    ## 117      76001     1666      Ismael Rodero Monteagudo 416.50      90
    ## 118      76001     1456                  Hector Giron 364.00      30
    ## 119      76002     1652                  Hector Giron 413.00      60
    ## 120      76002     1153        Hector Aragones Frutos 288.25      90
    ## 121      76001     1668                  Hector Giron 417.00      60
    ## 122      76001     1315       Fernando Mariano Berrio 328.75      90
    ## 123      76002     1695 Juan Francisco Portillo Gomez 423.75      90
    ## 124      76002     1618              Felipe Villatoro 404.50      30
    ## 125      76002     1912          Angel Valdez Alegria 478.00      30
    ## 126      76002     1112              Felipe Villatoro 278.00      90
    ## 127      76001      828              Felipe Villatoro 207.00      90
    ## 128      76001     1820          Pedro Alvarez Parejo 455.00      30
    ## 129      76002      306          Pedro Alvarez Parejo  76.50      90
    ## 130      76001     1459        Hector Aragones Frutos 364.75      30
    ## 131      76002     1230          Angel Valdez Alegria 307.50      90
    ## 132      76002      456 Juan Francisco Portillo Gomez 114.00      30
    ## 133      76002      248          Pedro Alvarez Parejo  62.00      30
    ## 134      76001      237       Fernando Mariano Berrio  59.25      30
    ## 135      76002     1280       Fernando Mariano Berrio 320.00      60
    ## 136      76001     1193              Felipe Villatoro 298.25      30
    ## 137      76001     1294                  Hector Giron 323.50      90
    ## 138      76001     1435          Pedro Alvarez Parejo 358.75      90
    ## 139      76002     1589        Hector Aragones Frutos 397.25      30
    ## 140      76001     1259          Angel Valdez Alegria 314.75      90
    ## 141      76002     1544      Ismael Rodero Monteagudo 386.00      60
    ## 142      76001      894 Juan Francisco Portillo Gomez 223.50      60
    ## 143      76001     1764                  Hector Giron 441.00      90
    ## 144      76001      540          Angel Valdez Alegria 135.00      30
    ## 145      76001     1383              Felipe Villatoro 345.75      60
    ## 146      76001      288             Luis Jaime Urbano  72.00      60
    ## 147      76001      636        Hector Aragones Frutos 159.00      90
    ## 148      76001      311          Angel Valdez Alegria  77.75      60
    ## 149      76001      936       Fernando Mariano Berrio 234.00      90
    ## 150      76002     1607       Fernando Mariano Berrio 401.75      30
    ## 151      76002     1459                  Hector Giron 364.75      60
    ## 152      76001      743             Luis Jaime Urbano 185.75      60
    ## 153      76002     1952                  Hector Giron 488.00      30
    ## 154      76001     1575              Felipe Villatoro 393.75      30
    ## 155      76001      344          Pedro Alvarez Parejo  86.00      90
    ## 156      76001      215          Angel Valdez Alegria  53.75      60
    ## 157      76001     1685 Juan Francisco Portillo Gomez 421.25      90
    ## 158      76001     1904          Angel Valdez Alegria 476.00      30
    ## 159      76001      974                  Hector Giron 243.50      30
    ## 160      76001      369              Felipe Villatoro  92.25      30
    ## 161      76001      609      Ismael Rodero Monteagudo 152.25      90
    ## 162      76002      209       Fernando Mariano Berrio  52.25      60
    ## 163      76001     1814      Ismael Rodero Monteagudo 453.50      60
    ## 164      76002     1729      Ismael Rodero Monteagudo 432.25      30
    ## 165      76001      349        Hector Aragones Frutos  87.25      60
    ## 166      76001      890             Luis Jaime Urbano 222.50      30
    ## 167      76001      557       Fernando Mariano Berrio 139.25      60
    ## 168      76001      726             Luis Jaime Urbano 181.50      90
    ## 169      76002     1545 Juan Francisco Portillo Gomez 386.25      30
    ## 170      76001      596          Pedro Alvarez Parejo 149.00      90
    ## 171      76001     1232             Luis Jaime Urbano 308.00      60
    ## 172      76001     1442       Fernando Mariano Berrio 360.50      30
    ## 173      76001     1245          Angel Valdez Alegria 311.25      30
    ## 174      76002     1398          Angel Valdez Alegria 349.50      60
    ## 175      76002     1305 Juan Francisco Portillo Gomez 326.25      30
    ## 176      76002      630              Felipe Villatoro 157.50      60
    ## 177      76002     1047             Luis Jaime Urbano 261.75      30
    ## 178      76002     1235          Angel Valdez Alegria 308.75      60
    ## 179      76002     1271              Felipe Villatoro 317.75      60
    ## 180      76002      862          Pedro Alvarez Parejo 215.50      30
    ## 181      76002     1345 Juan Francisco Portillo Gomez 336.25      60
    ## 182      76001     1044          Angel Valdez Alegria 261.00      30
    ## 183      76002     1876 Juan Francisco Portillo Gomez 469.00      60
    ## 184      76002      898      Ismael Rodero Monteagudo 224.50      60
    ## 185      76001     1398        Hector Aragones Frutos 349.50      30
    ## 186      76002     1719          Pedro Alvarez Parejo 429.75      30
    ## 187      76001     1847          Angel Valdez Alegria 461.75      30
    ## 188      76002      407          Pedro Alvarez Parejo 101.75      90
    ## 189      76001     1699       Fernando Mariano Berrio 424.75      90
    ## 190      76002     1061                  Hector Giron 265.25      90
    ## 191      76002     1447                  Hector Giron 361.75      60
    ## 192      76001      496      Ismael Rodero Monteagudo 124.00      90
    ## 193      76001      568 Juan Francisco Portillo Gomez 142.00      60
    ## 194      76001      739 Juan Francisco Portillo Gomez 184.75      90
    ## 195      76001      322             Luis Jaime Urbano  80.50      60
    ## 196      76001      496             Luis Jaime Urbano 124.00      60
    ## 197      76002     1640        Hector Aragones Frutos 410.00      30
    ## 198      76002      955          Pedro Alvarez Parejo 238.75      30
    ## 199      76001     1697                  Hector Giron 424.25      90
    ## 200      76001     1756          Angel Valdez Alegria 439.00      60
    ## 201      76001     1283          Angel Valdez Alegria 320.75      60
    ## 202      76001      708              Felipe Villatoro 177.00      30
    ## 203      76002     1509                  Hector Giron 377.25      90
    ## 204      76001     1333          Angel Valdez Alegria 333.25      90
    ## 205      76002     1536              Felipe Villatoro 384.00      90
    ## 206      76001     1062        Hector Aragones Frutos 265.50      30
    ## 207      76002     1929              Felipe Villatoro 482.25      30
    ## 208      76001     1698                  Hector Giron 424.50      90
    ## 209      76001      294          Pedro Alvarez Parejo  73.50      60
    ## 210      76002      709                  Hector Giron 177.25      60
    ## 211      76002     1817 Juan Francisco Portillo Gomez 454.25      90
    ## 212      76002     1080       Fernando Mariano Berrio 270.00      60
    ## 213      76002     1761             Luis Jaime Urbano 440.25      30
    ## 214      76001     1366             Luis Jaime Urbano 341.50      30
    ## 215      76001      852          Angel Valdez Alegria 213.00      30
    ## 216      76001     1421       Fernando Mariano Berrio 355.25      30
    ## 217      76001      919        Hector Aragones Frutos 229.75      30
    ## 218      76001     1163                  Hector Giron 290.75      90
    ## 219      76002     1775      Ismael Rodero Monteagudo 443.75      90
    ## 220      76002     1714        Hector Aragones Frutos 428.50      60
    ## 221      76002     1387          Angel Valdez Alegria 346.75      60
    ## 222      76001      749              Felipe Villatoro 187.25      30
    ## 223      76002     1763       Fernando Mariano Berrio 440.75      30
    ## 224      76001     1416             Luis Jaime Urbano 354.00      60
    ## 225      76001     1471              Felipe Villatoro 367.75      30
    ## 226      76002     1846          Angel Valdez Alegria 461.50      60
    ## 227      76001      555          Angel Valdez Alegria 138.75      30
    ## 228      76002     1669              Felipe Villatoro 417.25      60
    ## 229      76002     1081      Ismael Rodero Monteagudo 270.25      30
    ## 230      76001      729              Felipe Villatoro 182.25      60
    ## 231      76001     1132          Angel Valdez Alegria 283.00      90
    ## 232      76001      291       Fernando Mariano Berrio  72.75      30
    ## 233      76001     1768              Felipe Villatoro 442.00      60
    ## 234      76002     1798       Fernando Mariano Berrio 449.50      30
    ## 235      76002      206 Juan Francisco Portillo Gomez  51.50      90
    ## 236      76001     1295              Felipe Villatoro 323.75      30
    ## 237      76002      532          Angel Valdez Alegria 133.00      60
    ## 238      76002      732        Hector Aragones Frutos 183.00      90
    ## 239      76002      698          Angel Valdez Alegria 174.50      90
    ## 240      76001     1101        Hector Aragones Frutos 275.25      90
    ## 241      76001     1155        Hector Aragones Frutos 288.75      60
    ## 242      76001     1577                  Hector Giron 394.25      30
    ## 243      76001     1342          Angel Valdez Alegria 335.50      90
    ## 244      76001     1427             Luis Jaime Urbano 356.75      60
    ## 245      76001     1490 Juan Francisco Portillo Gomez 372.50      60
    ## 246      76002      627              Felipe Villatoro 156.75      90
    ## 247      76001     1661 Juan Francisco Portillo Gomez 415.25      60
    ## 248      76001     1098      Ismael Rodero Monteagudo 274.50      30
    ## 249      76001     1941          Pedro Alvarez Parejo 485.25      90
    ## 250      76001     1302          Angel Valdez Alegria 325.50      60
    ## 251      76001     1498              Felipe Villatoro 374.50      30
    ## 252      76002      521          Pedro Alvarez Parejo 130.25      90
    ## 253      76002     1714 Juan Francisco Portillo Gomez 428.50      60
    ## 254      76001      280 Juan Francisco Portillo Gomez  70.00      30
    ## 255      76001     1867          Angel Valdez Alegria 466.75      30
    ## 256      76002      347       Fernando Mariano Berrio  86.75      60
    ## 257      76001      955              Felipe Villatoro 238.75      30
    ## 258      76001     1126              Felipe Villatoro 281.50      90
    ## 259      76002      225        Hector Aragones Frutos  56.25      30
    ## 260      76001      479        Hector Aragones Frutos 119.75      60
    ## 261      76002     1054                  Hector Giron 263.50      30
    ## 262      76001     1582 Juan Francisco Portillo Gomez 395.50      60
    ## 263      76002      222      Ismael Rodero Monteagudo  55.50      30
    ## 264      76001     1307 Juan Francisco Portillo Gomez 326.75      90
    ## 265      76001      969 Juan Francisco Portillo Gomez 242.25      60
    ## 266      76002     1750          Angel Valdez Alegria 437.50      60
    ## 267      76001      679                  Hector Giron 169.75      30
    ## 268      76001      788      Ismael Rodero Monteagudo 197.00      30
    ## 269      76002      723 Juan Francisco Portillo Gomez 180.75      60
    ## 270      76002     1913      Ismael Rodero Monteagudo 478.25      60
    ## 271      76002      665 Juan Francisco Portillo Gomez 166.25      60
    ## 272      76002      930      Ismael Rodero Monteagudo 232.50      30
    ## 273      76001     1003              Felipe Villatoro 250.75      30
    ## 274      76002      613       Fernando Mariano Berrio 153.25      60
    ## 275      76001      252             Luis Jaime Urbano  63.00      30
    ## 276      76002     1698       Fernando Mariano Berrio 424.50      90
    ## 277      76002      956       Fernando Mariano Berrio 239.00      30
    ## 278      76001      830        Hector Aragones Frutos 207.50      60
    ## 279      76002     1071             Luis Jaime Urbano 267.75      90
    ## 280      76001      602        Hector Aragones Frutos 150.50      30
    ## 281      76002     1890          Angel Valdez Alegria 472.50      60
    ## 282      76002     1301                  Hector Giron 325.25      90
    ## 283      76001     1523          Pedro Alvarez Parejo 380.75      60
    ## 284      76001     1273                  Hector Giron 318.25      90
    ## 285      76002     1832 Juan Francisco Portillo Gomez 458.00      30
    ## 286      76002     1956          Pedro Alvarez Parejo 489.00      90
    ## 287      76002     1026              Felipe Villatoro 256.50      60
    ## 288      76002     1025             Luis Jaime Urbano 256.25      60
    ## 289      76001     1526          Pedro Alvarez Parejo 381.50      60
    ## 290      76002     1361        Hector Aragones Frutos 340.25      90
    ## 291      76001     1872             Luis Jaime Urbano 468.00      90
    ## 292      76001      350      Ismael Rodero Monteagudo  87.50      90
    ## 293      76002     1185             Luis Jaime Urbano 296.25      30
    ## 294      76001     1568      Ismael Rodero Monteagudo 392.00      30
    ## 295      76002     1608 Juan Francisco Portillo Gomez 402.00      30
    ## 296      76002      645             Luis Jaime Urbano 161.25      30
    ## 297      76001      244          Pedro Alvarez Parejo  61.00      60
    ## 298      76001      615          Angel Valdez Alegria 153.75      60
    ## 299      76002     1897          Pedro Alvarez Parejo 474.25      60
    ## 300      76002      786             Luis Jaime Urbano 196.50      60
    ## 301      76001      887 Juan Francisco Portillo Gomez 221.75      90
    ## 302      76001     1604              Felipe Villatoro 401.00      90
    ## 303      76002     1840          Pedro Alvarez Parejo 460.00      30
    ## 304      76001     1008        Hector Aragones Frutos 252.00      90
    ## 305      76002     1926 Juan Francisco Portillo Gomez 481.50      30
    ## 306      76002      737          Pedro Alvarez Parejo 184.25      90
    ## 307      76001     1876       Fernando Mariano Berrio 469.00      60
    ## 308      76001      336             Luis Jaime Urbano  84.00      60
    ## 309      76002      489          Pedro Alvarez Parejo 122.25      30
    ## 310      76002      227 Juan Francisco Portillo Gomez  56.75      60
    ## 311      76001     1440          Pedro Alvarez Parejo 360.00      30
    ## 312      76001     1220        Hector Aragones Frutos 305.00      60
    ## 313      76001     1561      Ismael Rodero Monteagudo 390.25      30
    ## 314      76002     1988          Pedro Alvarez Parejo 497.00      60
    ## 315      76001      278        Hector Aragones Frutos  69.50      60
    ## 316      76001     1227             Luis Jaime Urbano 306.75      60
    ## 317      76001     1700                  Hector Giron 425.00      60
    ## 318      76001     1563          Angel Valdez Alegria 390.75      60
    ## 319      76002      890        Hector Aragones Frutos 222.50      90
    ## 320      76002     1780              Felipe Villatoro 445.00      60
    ## 321      76002      745                  Hector Giron 186.25      90
    ## 322      76002      906          Pedro Alvarez Parejo 226.50      60
    ## 323      76002      478          Angel Valdez Alegria 119.50      60
    ## 324      76002     1739      Ismael Rodero Monteagudo 434.75      30
    ## 325      76001      212          Pedro Alvarez Parejo  53.00      60
    ## 326      76002     1504 Juan Francisco Portillo Gomez 376.00      30
    ## 327      76002      789                  Hector Giron 197.25      90
    ## 328      76002     1521      Ismael Rodero Monteagudo 380.25      90
    ## 329      76002     1282                  Hector Giron 320.50      30
    ## 330      76002      831 Juan Francisco Portillo Gomez 207.75      30
    ## 331      76002      570             Luis Jaime Urbano 142.50      90
    ## 332      76001      682        Hector Aragones Frutos 170.50      30
    ## 333      76001     1055      Ismael Rodero Monteagudo 263.75      90
    ## 334      76001      765        Hector Aragones Frutos 191.25      60
    ## 335      76002     1886                  Hector Giron 471.50      30
    ## 336      76001     1085 Juan Francisco Portillo Gomez 271.25      90
    ## 337      76002      732             Luis Jaime Urbano 183.00      30
    ## 338      76002      554              Felipe Villatoro 138.50      30
    ## 339      76002      236                  Hector Giron  59.00      60
    ## 340      76001     1700       Fernando Mariano Berrio 425.00      90
    ## 341      76001     1460          Angel Valdez Alegria 365.00      30
    ## 342      76002     1435        Hector Aragones Frutos 358.75      60
    ## 343      76002     1471       Fernando Mariano Berrio 367.75      30
    ## 344      76002      761          Pedro Alvarez Parejo 190.25      30
    ## 345      76002     1148          Angel Valdez Alegria 287.00      90
    ## 346      76002      692                  Hector Giron 173.00      90
    ## 347      76002      253      Ismael Rodero Monteagudo  63.25      90
    ## 348      76001     1312 Juan Francisco Portillo Gomez 328.00      30
    ## 349      76002      841          Angel Valdez Alegria 210.25      60
    ## 350      76002      294       Fernando Mariano Berrio  73.50      30
    ## 351      76001     1454          Pedro Alvarez Parejo 363.50      90
    ## 352      76001     1445                  Hector Giron 361.25      30
    ## 353      76001     1926          Pedro Alvarez Parejo 481.50      30
    ## 354      76002     1774             Luis Jaime Urbano 443.50      30
    ## 355      76002     1970              Felipe Villatoro 492.50      90
    ## 356      76002     1577      Ismael Rodero Monteagudo 394.25      60
    ## 357      76001      238      Ismael Rodero Monteagudo  59.50      90
    ## 358      76002      354          Angel Valdez Alegria  88.50      60
    ## 359      76002     1944       Fernando Mariano Berrio 486.00      60
    ## 360      76001      970      Ismael Rodero Monteagudo 242.50      90
    ## 361      76002     1993                  Hector Giron 498.25      90
    ## 362      76002     1777       Fernando Mariano Berrio 444.25      60
    ## 363      76001     1915             Luis Jaime Urbano 478.75      90
    ## 364      76002     1267       Fernando Mariano Berrio 316.75      30
    ## 365      76002      950              Felipe Villatoro 237.50      90
    ## 366      76002     1710        Hector Aragones Frutos 427.50      30
    ## 367      76002      905              Felipe Villatoro 226.25      90
    ## 368      76001     1866             Luis Jaime Urbano 466.50      60
    ## 369      76001      210             Luis Jaime Urbano  52.50      60
    ## 370      76001     1402       Fernando Mariano Berrio 350.50      90
    ## 371      76002      398             Luis Jaime Urbano  99.50      60
    ## 372      76001     1172          Pedro Alvarez Parejo 293.00      60
    ## 373      76002      945          Angel Valdez Alegria 236.25      90
    ## 374      76002      402             Luis Jaime Urbano 100.50      30
    ## 375      76001      200          Pedro Alvarez Parejo  50.00      90
    ## 376      76002     1639      Ismael Rodero Monteagudo 409.75      60
    ## 377      76001      264             Luis Jaime Urbano  66.00      60
    ## 378      76002      733          Pedro Alvarez Parejo 183.25      60
    ## 379      76002      336              Felipe Villatoro  84.00      90
    ## 380      76001     1304          Angel Valdez Alegria 326.00      60
    ## 381      76001      620             Luis Jaime Urbano 155.00      60
    ## 382      76001      693          Angel Valdez Alegria 173.25      30
    ## 383      76002     1480          Angel Valdez Alegria 370.00      30
    ## 384      76001     1225             Luis Jaime Urbano 306.25      90
    ## 385      76001      600          Pedro Alvarez Parejo 150.00      60
    ## 386      76002      373       Fernando Mariano Berrio  93.25      60
    ## 387      76002      442              Felipe Villatoro 110.50      60
    ## 388      76001     1616       Fernando Mariano Berrio 404.00      30
    ## 389      76002     1099              Felipe Villatoro 274.75      90
    ## 390      76001      787              Felipe Villatoro 196.75      30
    ## 391      76001     1314 Juan Francisco Portillo Gomez 328.50      90
    ## 392      76001      862      Ismael Rodero Monteagudo 215.50      60
    ## 393      76002      445          Pedro Alvarez Parejo 111.25      30
    ## 394      76001      485      Ismael Rodero Monteagudo 121.25      30
    ## 395      76002      266        Hector Aragones Frutos  66.50      90
    ## 396      76001     1979      Ismael Rodero Monteagudo 494.75      30
    ## 397      76001     1116              Felipe Villatoro 279.00      30
    ## 398      76002      384          Angel Valdez Alegria  96.00      90
    ## 399      76002      599 Juan Francisco Portillo Gomez 149.75      30
    ## 400      76002      388                  Hector Giron  97.00      90
    ## 401      76001     1164        Hector Aragones Frutos 291.00      30
    ## 402      76001     1945       Fernando Mariano Berrio 486.25      90
    ## 403      76002      724 Juan Francisco Portillo Gomez 181.00      60
    ## 404      76002      412          Angel Valdez Alegria 103.00      60
    ## 405      76001      807 Juan Francisco Portillo Gomez 201.75      60
    ## 406      76002     1950       Fernando Mariano Berrio 487.50      90
    ## 407      76002     1957      Ismael Rodero Monteagudo 489.25      30
    ## 408      76002     1664      Ismael Rodero Monteagudo 416.00      30
    ## 409      76001     1126             Luis Jaime Urbano 281.50      30
    ## 410      76001     1328              Felipe Villatoro 332.00      90
    ## 411      76002      336      Ismael Rodero Monteagudo  84.00      30
    ## 412      76001     1893          Pedro Alvarez Parejo 473.25      60
    ## 413      76002      680       Fernando Mariano Berrio 170.00      90
    ## 414      76001     1092        Hector Aragones Frutos 273.00      90
    ## 415      76002     1174              Felipe Villatoro 293.50      90
    ## 416      76001      737 Juan Francisco Portillo Gomez 184.25      30
    ## 417      76001      484       Fernando Mariano Berrio 121.00      60
    ## 418      76001      948       Fernando Mariano Berrio 237.00      60
    ## 419      76002     1312             Luis Jaime Urbano 328.00      90
    ## 420      76001     1030              Felipe Villatoro 257.50      90
    ## 421      76002     1903          Pedro Alvarez Parejo 475.75      30
    ## 422      76002      492 Juan Francisco Portillo Gomez 123.00      30
    ## 423      76001     1285       Fernando Mariano Berrio 321.25      60
    ## 424      76001      462              Felipe Villatoro 115.50      90
    ## 425      76002      294 Juan Francisco Portillo Gomez  73.50      30
    ## 426      76001     1722                  Hector Giron 430.50      60
    ## 427      76001      436              Felipe Villatoro 109.00      60
    ## 428      76001      271       Fernando Mariano Berrio  67.75      60
    ## 429      76002     1905        Hector Aragones Frutos 476.25      90
    ## 430      76001      833      Ismael Rodero Monteagudo 208.25      30
    ## 431      76001      224             Luis Jaime Urbano  56.00      60
    ## 432      76001      703      Ismael Rodero Monteagudo 175.75      60
    ## 433      76002      464      Ismael Rodero Monteagudo 116.00      60
    ## 434      76001     1238      Ismael Rodero Monteagudo 309.50      60
    ## 435      76002      462              Felipe Villatoro 115.50      60
    ## 436      76001     1917             Luis Jaime Urbano 479.25      30
    ## 437      76002      248      Ismael Rodero Monteagudo  62.00      90
    ## 438      76002     1270             Luis Jaime Urbano 317.50      90
    ## 439      76002     1973          Angel Valdez Alegria 493.25      60
    ## 440      76002      864        Hector Aragones Frutos 216.00      90
    ## 441      76002      424       Fernando Mariano Berrio 106.00      60
    ## 442      76001      312        Hector Aragones Frutos  78.00      60
    ## 443      76001     1788      Ismael Rodero Monteagudo 447.00      60
    ## 444      76002     1186        Hector Aragones Frutos 296.50      90
    ## 445      76001      414          Pedro Alvarez Parejo 103.50      30
    ## 446      76002      519                  Hector Giron 129.75      30
    ## 447      76002     1495       Fernando Mariano Berrio 373.75      30
    ## 448      76002      769                  Hector Giron 192.25      90
    ## 449      76001     1381          Angel Valdez Alegria 345.25      30
    ## 450      76001      690          Pedro Alvarez Parejo 172.50      30
    ## 451      76001     1593      Ismael Rodero Monteagudo 398.25      30
    ## 452      76001     1433             Luis Jaime Urbano 358.25      90
    ## 453      76002      713        Hector Aragones Frutos 178.25      60
    ## 454      76001      636                  Hector Giron 159.00      60
    ## 455      76001      638        Hector Aragones Frutos 159.50      60
    ## 456      76002     1708                  Hector Giron 427.00      30
    ## 457      76002     1202             Luis Jaime Urbano 300.50      30
    ## 458      76001      602          Angel Valdez Alegria 150.50      60
    ## 459      76001      323        Hector Aragones Frutos  80.75      60
    ## 460      76002      320      Ismael Rodero Monteagudo  80.00      60
    ## 461      76002      381              Felipe Villatoro  95.25      60
    ## 462      76001      535          Angel Valdez Alegria 133.75      60
    ## 463      76001      562             Luis Jaime Urbano 140.50      30
    ## 464      76002      950       Fernando Mariano Berrio 237.50      30
    ## 465      76002     1883      Ismael Rodero Monteagudo 470.75      60
    ## 466      76001     1690       Fernando Mariano Berrio 422.50      30
    ## 467      76001     1327              Felipe Villatoro 331.75      90
    ## 468      76001     1458             Luis Jaime Urbano 364.50      30
    ## 469      76001     1059          Angel Valdez Alegria 264.75      30
    ## 470      76001     1002             Luis Jaime Urbano 250.50      30
    ## 471      76001     1302          Angel Valdez Alegria 325.50      30
    ## 472      76002     1639      Ismael Rodero Monteagudo 409.75      60
    ## 473      76002      840        Hector Aragones Frutos 210.00      60
    ## 474      76002     1849             Luis Jaime Urbano 462.25      30
    ## 475      76002     1065             Luis Jaime Urbano 266.25      60
    ## 476      76001     1529      Ismael Rodero Monteagudo 382.25      60
    ## 477      76001      337      Ismael Rodero Monteagudo  84.25      90
    ## 478      76001      719        Hector Aragones Frutos 179.75      30
    ## 479      76001     1913                  Hector Giron 478.25      90
    ## 480      76001     1180          Pedro Alvarez Parejo 295.00      30
    ## 481      76002     1052          Pedro Alvarez Parejo 263.00      30
    ## 482      76001     1037          Pedro Alvarez Parejo 259.25      90
    ## 483      76001     1953      Ismael Rodero Monteagudo 488.25      30
    ## 484      76002     1083       Fernando Mariano Berrio 270.75      90
    ## 485      76001     1482              Felipe Villatoro 370.50      30
    ## 486      76001     1681          Angel Valdez Alegria 420.25      30
    ## 487      76002     1418      Ismael Rodero Monteagudo 354.50      30
    ## 488      76001     1285          Angel Valdez Alegria 321.25      60
    ## 489      76002      878      Ismael Rodero Monteagudo 219.50      90
    ## 490      76001      332          Angel Valdez Alegria  83.00      30
    ## 491      76001      256             Luis Jaime Urbano  64.00      30
    ## 492      76001     1724              Felipe Villatoro 431.00      60
    ## 493      76001     1996          Angel Valdez Alegria 499.00      90
    ## 494      76001     1097                  Hector Giron 274.25      60
    ## 495      76002     1009              Felipe Villatoro 252.25      90
    ## 496      76002     1730       Fernando Mariano Berrio 432.50      60
    ## 497      76001     1718 Juan Francisco Portillo Gomez 429.50      30
    ## 498      76002     1720        Hector Aragones Frutos 430.00      60
    ## 499      76002     1737             Luis Jaime Urbano 434.25      90
    ## 500      76002      590          Angel Valdez Alegria 147.50      60
    ## 501      76002     1040             Luis Jaime Urbano 260.00      60
    ## 502      76002      443             Luis Jaime Urbano 110.75      90
    ## 503      76001     1020      Ismael Rodero Monteagudo 255.00      60
    ## 504      76001     1309          Pedro Alvarez Parejo 327.25      30
    ## 505      76002      611      Ismael Rodero Monteagudo 152.75      60
    ## 506      76002     1941          Pedro Alvarez Parejo 485.25      60
    ## 507      76001      790                  Hector Giron 197.50      30
    ## 508      76002      372              Felipe Villatoro  93.00      30
    ## 509      76002     1808 Juan Francisco Portillo Gomez 452.00      30
    ## 510      76002      996       Fernando Mariano Berrio 249.00      60
    ## 511      76001     1580      Ismael Rodero Monteagudo 395.00      90
    ## 512      76001     1580             Luis Jaime Urbano 395.00      60
    ## 513      76001     1276              Felipe Villatoro 319.00      90
    ## 514      76002     1683       Fernando Mariano Berrio 420.75      60
    ## 515      76002     1055      Ismael Rodero Monteagudo 263.75      30
    ## 516      76002      814              Felipe Villatoro 203.50      30
    ## 517      76002      397        Hector Aragones Frutos  99.25      30
    ## 518      76002     1386        Hector Aragones Frutos 346.50      60
    ## 519      76001     1960          Angel Valdez Alegria 490.00      90
    ## 520      76002      229       Fernando Mariano Berrio  57.25      90
    ## 521      76001      831 Juan Francisco Portillo Gomez 207.75      60
    ## 522      76002     1720        Hector Aragones Frutos 430.00      30
    ## 523      76001     1811       Fernando Mariano Berrio 452.75      30
    ## 524      76001      319              Felipe Villatoro  79.75      30
    ## 525      76001     1414             Luis Jaime Urbano 353.50      60
    ## 526      76002     1097        Hector Aragones Frutos 274.25      90
    ## 527      76002     1859      Ismael Rodero Monteagudo 464.75      90
    ## 528      76002      440      Ismael Rodero Monteagudo 110.00      90
    ## 529      76001      499        Hector Aragones Frutos 124.75      60
    ## 530      76002     1396 Juan Francisco Portillo Gomez 349.00      90
    ## 531      76002      403                  Hector Giron 100.75      60
    ## 532      76002     1445                  Hector Giron 361.25      30
    ## 533      76001      378              Felipe Villatoro  94.50      30
    ## 534      76001      924       Fernando Mariano Berrio 231.00      60
    ## 535      76001     1444              Felipe Villatoro 361.00      90
    ## 536      76002      253          Angel Valdez Alegria  63.25      60
    ## 537      76001     1947       Fernando Mariano Berrio 486.75      30
    ## 538      76002     1563              Felipe Villatoro 390.75      30
    ## 539      76002      742        Hector Aragones Frutos 185.50      30
    ## 540      76002      243              Felipe Villatoro  60.75      90
    ## 541      76001     1506 Juan Francisco Portillo Gomez 376.50      30
    ## 542      76001     1889       Fernando Mariano Berrio 472.25      60
    ## 543      76002      531          Pedro Alvarez Parejo 132.75      90
    ## 544      76002     1037          Angel Valdez Alegria 259.25      90
    ## 545      76002     1692        Hector Aragones Frutos 423.00      30
    ## 546      76002      894              Felipe Villatoro 223.50      60
    ## 547      76002      504       Fernando Mariano Berrio 126.00      60
    ## 548      76002      665        Hector Aragones Frutos 166.25      30
    ## 549      76001      964          Angel Valdez Alegria 241.00      90
    ## 550      76002      743          Pedro Alvarez Parejo 185.75      30
    ## 551      76001     1193      Ismael Rodero Monteagudo 298.25      30
    ## 552      76002     1865       Fernando Mariano Berrio 466.25      60
    ## 553      76002     1456      Ismael Rodero Monteagudo 364.00      60
    ## 554      76001      772             Luis Jaime Urbano 193.00      30
    ## 555      76002      385 Juan Francisco Portillo Gomez  96.25      90
    ## 556      76001      591       Fernando Mariano Berrio 147.75      30
    ## 557      76001     1241             Luis Jaime Urbano 310.25      90
    ## 558      76002      794          Angel Valdez Alegria 198.50      90
    ## 559      76002     1944      Ismael Rodero Monteagudo 486.00      60
    ## 560      76001     1355              Felipe Villatoro 338.75      60
    ## 561      76002      474          Angel Valdez Alegria 118.50      90
    ## 562      76001     1014          Pedro Alvarez Parejo 253.50      60
    ## 563      76002      906              Felipe Villatoro 226.50      90
    ## 564      76001      408       Fernando Mariano Berrio 102.00      30
    ## 565      76001      873                  Hector Giron 218.25      90
    ## 566      76002      905             Luis Jaime Urbano 226.25      90
    ## 567      76001     1249             Luis Jaime Urbano 312.25      30
    ## 568      76002     1040        Hector Aragones Frutos 260.00      90
    ## 569      76002      467        Hector Aragones Frutos 116.75      30
    ## 570      76001     1294      Ismael Rodero Monteagudo 323.50      30
    ## 571      76001     1497             Luis Jaime Urbano 374.25      30
    ## 572      76001     1481                  Hector Giron 370.25      90
    ## 573      76001     1378          Angel Valdez Alegria 344.50      90
    ## 574      76002      809          Pedro Alvarez Parejo 202.25      90
    ## 575      76001      856      Ismael Rodero Monteagudo 214.00      90
    ## 576      76001      558        Hector Aragones Frutos 139.50      30
    ## 577      76002      280                  Hector Giron  70.00      90
    ## 578      76001     1049          Angel Valdez Alegria 262.25      60
    ## 579      76001      533              Felipe Villatoro 133.25      90
    ## 580      76002     1788                  Hector Giron 447.00      90
    ## 581      76001     1987             Luis Jaime Urbano 496.75      60
    ## 582      76002      649              Felipe Villatoro 162.25      30
    ## 583      76002      924        Hector Aragones Frutos 231.00      30
    ## 584      76002     1086      Ismael Rodero Monteagudo 271.50      90
    ## 585      76002     1505          Angel Valdez Alegria 376.25      30
    ## 586      76001     1532             Luis Jaime Urbano 383.00      90
    ## 587      76002      502          Pedro Alvarez Parejo 125.50      90
    ## 588      76001     1108                  Hector Giron 277.00      90
    ## 589      76001     1197             Luis Jaime Urbano 299.25      90
    ## 590      76002      761       Fernando Mariano Berrio 190.25      30
    ## 591      76001     1274                  Hector Giron 318.50      30
    ## 592      76001      826          Pedro Alvarez Parejo 206.50      30
    ## 593      76001      485        Hector Aragones Frutos 121.25      60
    ## 594      76001      311          Pedro Alvarez Parejo  77.75      90
    ## 595      76002     1457          Pedro Alvarez Parejo 364.25      60
    ## 596      76001      410             Luis Jaime Urbano 102.50      30
    ## 597      76002     1679       Fernando Mariano Berrio 419.75      90
    ## 598      76002      700          Pedro Alvarez Parejo 175.00      60
    ## 599      76002      809          Pedro Alvarez Parejo 202.25      60
    ## 600      76002      529          Pedro Alvarez Parejo 132.25      90
    ## 601      76001     1078        Hector Aragones Frutos 269.50      90
    ## 602      76001     1086          Angel Valdez Alegria 271.50      60
    ## 603      76001      465              Felipe Villatoro 116.25      90
    ## 604      76001      291        Hector Aragones Frutos  72.75      30
    ## 605      76001     1684                  Hector Giron 421.00      60
    ## 606      76002      455      Ismael Rodero Monteagudo 113.75      60
    ## 607      76001     1131          Pedro Alvarez Parejo 282.75      60
    ## 608      76002     1104              Felipe Villatoro 276.00      90
    ## 609      76001     1827                  Hector Giron 456.75      90
    ## 610      76001      504      Ismael Rodero Monteagudo 126.00      30
    ## 611      76001     1016              Felipe Villatoro 254.00      60
    ## 612      76001      461          Angel Valdez Alegria 115.25      90
    ## 613      76001     1368                  Hector Giron 342.00      30
    ## 614      76001     1049          Pedro Alvarez Parejo 262.25      60
    ## 615      76002      718       Fernando Mariano Berrio 179.50      60
    ## 616      76001     1317          Angel Valdez Alegria 329.25      90
    ## 617      76002     1945       Fernando Mariano Berrio 486.25      90
    ## 618      76001      247                  Hector Giron  61.75      30
    ## 619      76001      980                  Hector Giron 245.00      90
    ## 620      76002      326 Juan Francisco Portillo Gomez  81.50      60
    ## 621      76002     1956          Pedro Alvarez Parejo 489.00      30
    ## 622      76002      902       Fernando Mariano Berrio 225.50      60
    ## 623      76001     1147          Angel Valdez Alegria 286.75      60
    ## 624      76002      539             Luis Jaime Urbano 134.75      90
    ## 625      76002     1113          Angel Valdez Alegria 278.25      60
    ## 626      76001     1103          Pedro Alvarez Parejo 275.75      90
    ## 627      76001      303             Luis Jaime Urbano  75.75      60
    ## 628      76001     1546       Fernando Mariano Berrio 386.50      60
    ## 629      76002      294          Pedro Alvarez Parejo  73.50      90
    ## 630      76001     1694       Fernando Mariano Berrio 423.50      30
    ## 631      76001     1416                  Hector Giron 354.00      60
    ## 632      76002     1481        Hector Aragones Frutos 370.25      30
    ## 633      76001     1838             Luis Jaime Urbano 459.50      60
    ## 634      76002     1487             Luis Jaime Urbano 371.75      60
    ## 635      76001     1074        Hector Aragones Frutos 268.50      90
    ## 636      76001     1741        Hector Aragones Frutos 435.25      60
    ## 637      76002     1458        Hector Aragones Frutos 364.50      60
    ## 638      76001      813       Fernando Mariano Berrio 203.25      90
    ## 639      76001      856             Luis Jaime Urbano 214.00      60
    ## 640      76002      650              Felipe Villatoro 162.50      30
    ## 641      76002      567          Angel Valdez Alegria 141.75      30
    ## 642      76001     1256        Hector Aragones Frutos 314.00      30
    ## 643      76001      218             Luis Jaime Urbano  54.50      90
    ## 644      76001      867          Pedro Alvarez Parejo 216.75      30
    ## 645      76001      913      Ismael Rodero Monteagudo 228.25      60
    ## 646      76002     1512          Angel Valdez Alegria 378.00      60
    ## 647      76002      203                  Hector Giron  50.75      90
    ## 648      76001     1012          Angel Valdez Alegria 253.00      60
    ## 649      76001     1122        Hector Aragones Frutos 280.50      30
    ## 650      76002     1880                  Hector Giron 470.00      90
    ## 651      76002      751          Angel Valdez Alegria 187.75      60
    ## 652      76001     1886          Pedro Alvarez Parejo 471.50      60
    ## 653      76002      363                  Hector Giron  90.75      90
    ## 654      76001      566 Juan Francisco Portillo Gomez 141.50      30
    ## 655      76002     1330              Felipe Villatoro 332.50      90
    ## 656      76002     1385 Juan Francisco Portillo Gomez 346.25      90
    ## 657      76002     1880             Luis Jaime Urbano 470.00      90
    ## 658      76002     1704          Angel Valdez Alegria 426.00      90
    ## 659      76002      214      Ismael Rodero Monteagudo  53.50      60
    ## 660      76001      665       Fernando Mariano Berrio 166.25      60
    ## 661      76001     1950        Hector Aragones Frutos 487.50      90
    ## 662      76002      500          Angel Valdez Alegria 125.00      90
    ## 663      76002      990                  Hector Giron 247.50      90
    ## 664      76002     1551        Hector Aragones Frutos 387.75      30
    ## 665      76002      613       Fernando Mariano Berrio 153.25      60
    ## 666      76001     1571       Fernando Mariano Berrio 392.75      60
    ## 667      76001      794       Fernando Mariano Berrio 198.50      60
    ## 668      76002     1707              Felipe Villatoro 426.75      60
    ## 669      76002     1343                  Hector Giron 335.75      60
    ## 670      76002     1022                  Hector Giron 255.50      90
    ## 671      76002      413      Ismael Rodero Monteagudo 103.25      60
    ## 672      76002      690          Angel Valdez Alegria 172.50      90
    ## 673      76002      576          Pedro Alvarez Parejo 144.00      30
    ## 674      76002      769 Juan Francisco Portillo Gomez 192.25      60
    ## 675      76002      735          Pedro Alvarez Parejo 183.75      30
    ## 676      76002      578       Fernando Mariano Berrio 144.50      30
    ## 677      76002     1126 Juan Francisco Portillo Gomez 281.50      30
    ## 678      76002      907                  Hector Giron 226.75      90
    ## 679      76001     1842       Fernando Mariano Berrio 460.50      90
    ## 680      76002      651                  Hector Giron 162.75      90
    ## 681      76001      701       Fernando Mariano Berrio 175.25      90
    ## 682      76002      733             Luis Jaime Urbano 183.25      60
    ## 683      76002     1571        Hector Aragones Frutos 392.75      60
    ## 684      76002      405        Hector Aragones Frutos 101.25      30
    ## 685      76001      872          Angel Valdez Alegria 218.00      30
    ## 686      76001     1167       Fernando Mariano Berrio 291.75      60
    ## 687      76002     1867      Ismael Rodero Monteagudo 466.75      60
    ## 688      76002     1975          Pedro Alvarez Parejo 493.75      30
    ## 689      76001      900      Ismael Rodero Monteagudo 225.00      60
    ## 690      76001     1400 Juan Francisco Portillo Gomez 350.00      30
    ## 691      76002      272          Pedro Alvarez Parejo  68.00      90
    ## 692      76002      358 Juan Francisco Portillo Gomez  89.50      60
    ## 693      76002     1951 Juan Francisco Portillo Gomez 487.75      60
    ## 694      76002      807        Hector Aragones Frutos 201.75      30
    ## 695      76002     1748          Angel Valdez Alegria 437.00      30
    ## 696      76001     1485        Hector Aragones Frutos 371.25      60
    ## 697      76002     1150      Ismael Rodero Monteagudo 287.50      60
    ## 698      76002      215          Angel Valdez Alegria  53.75      90
    ## 699      76001      359                  Hector Giron  89.75      60
    ## 700      76001      856       Fernando Mariano Berrio 214.00      60
    ## 701      76001      298          Angel Valdez Alegria  74.50      90
    ## 702      76002      918      Ismael Rodero Monteagudo 229.50      60
    ## 703      76002     1093 Juan Francisco Portillo Gomez 273.25      60
    ## 704      76001     1713 Juan Francisco Portillo Gomez 428.25      30
    ## 705      76001     1763          Angel Valdez Alegria 440.75      60
    ## 706      76002     1809              Felipe Villatoro 452.25      30
    ## 707      76001     1349      Ismael Rodero Monteagudo 337.25      90
    ## 708      76002      511       Fernando Mariano Berrio 127.75      30
    ## 709      76001      718              Felipe Villatoro 179.50      30
    ## 710      76001      930              Felipe Villatoro 232.50      60
    ## 711      76001      272       Fernando Mariano Berrio  68.00      30
    ## 712      76001     1804          Pedro Alvarez Parejo 451.00      30
    ## 713      76001     1373       Fernando Mariano Berrio 343.25      30
    ## 714      76001      800              Felipe Villatoro 200.00      60
    ## 715      76001     1638          Pedro Alvarez Parejo 409.50      60
    ## 716      76002      591          Angel Valdez Alegria 147.75      30
    ## 717      76002      823 Juan Francisco Portillo Gomez 205.75      90
    ## 718      76001     1302          Angel Valdez Alegria 325.50      30
    ## 719      76002      889          Pedro Alvarez Parejo 222.25      90
    ## 720      76002     1496       Fernando Mariano Berrio 374.00      60
    ## 721      76001     1394        Hector Aragones Frutos 348.50      60
    ## 722      76002     1905        Hector Aragones Frutos 476.25      90
    ## 723      76002      218             Luis Jaime Urbano  54.50      60
    ## 724      76001     1445      Ismael Rodero Monteagudo 361.25      90
    ## 725      76002     1581      Ismael Rodero Monteagudo 395.25      90
    ## 726      76001     1407       Fernando Mariano Berrio 351.75      90
    ## 727      76001      557              Felipe Villatoro 139.25      90
    ## 728      76002     1636             Luis Jaime Urbano 409.00      30
    ## 729      76001     1784                  Hector Giron 446.00      60
    ## 730      76001      718        Hector Aragones Frutos 179.50      30
    ## 731      76001      257        Hector Aragones Frutos  64.25      60
    ## 732      76001      425       Fernando Mariano Berrio 106.25      90
    ## 733      76001      685        Hector Aragones Frutos 171.25      90
    ## 734      76001      861             Luis Jaime Urbano 215.25      60
    ## 735      76002     1024                  Hector Giron 256.00      30
    ## 736      76001     1180        Hector Aragones Frutos 295.00      30
    ## 737      76001     1595              Felipe Villatoro 398.75      30
    ## 738      76001      237          Angel Valdez Alegria  59.25      90
    ## 739      76001      227             Luis Jaime Urbano  56.75      90
    ## 740      76001     1695 Juan Francisco Portillo Gomez 423.75      30
    ## 741      76001     1666              Felipe Villatoro 416.50      90
    ## 742      76001      914                  Hector Giron 228.50      60
    ## 743      76001     1168              Felipe Villatoro 292.00      60
    ## 744      76001     1958      Ismael Rodero Monteagudo 489.50      60
    ## 745      76001      318       Fernando Mariano Berrio  79.50      30
    ## 746      76002     1637 Juan Francisco Portillo Gomez 409.25      30
    ## 747      76001      923      Ismael Rodero Monteagudo 230.75      60
    ## 748      76001     1346             Luis Jaime Urbano 336.50      30
    ## 749      76002      817             Luis Jaime Urbano 204.25      90
    ## 750      76001     1948        Hector Aragones Frutos 487.00      90
    ## 751      76001     1293        Hector Aragones Frutos 323.25      30
    ## 752      76001      300        Hector Aragones Frutos  75.00      30
    ## 753      76001     1908                  Hector Giron 477.00      30
    ## 754      76002      946             Luis Jaime Urbano 236.50      60
    ## 755      76002     1494       Fernando Mariano Berrio 373.50      30
    ## 756      76001      269          Angel Valdez Alegria  67.25      90
    ## 757      76002     1608       Fernando Mariano Berrio 402.00      60
    ## 758      76002     1348             Luis Jaime Urbano 337.00      60
    ## 759      76002     1090       Fernando Mariano Berrio 272.50      60
    ## 760      76002      417              Felipe Villatoro 104.25      90
    ## 761      76001     1748 Juan Francisco Portillo Gomez 437.00      60
    ## 762      76002      945          Angel Valdez Alegria 236.25      90
    ## 763      76002     1823             Luis Jaime Urbano 455.75      60
    ## 764      76002     1805              Felipe Villatoro 451.25      30
    ## 765      76001      243      Ismael Rodero Monteagudo  60.75      30
    ## 766      76002     1198 Juan Francisco Portillo Gomez 299.50      90
    ## 767      76001      630        Hector Aragones Frutos 157.50      30
    ## 768      76002      218              Felipe Villatoro  54.50      90
    ## 769      76002      239          Pedro Alvarez Parejo  59.75      30
    ## 770      76002     1585      Ismael Rodero Monteagudo 396.25      30
    ## 771      76002     1640        Hector Aragones Frutos 410.00      60
    ## 772      76002      723                  Hector Giron 180.75      30
    ## 773      76002      766      Ismael Rodero Monteagudo 191.50      90
    ## 774      76001      509             Luis Jaime Urbano 127.25      30
    ## 775      76001      243       Fernando Mariano Berrio  60.75      30
    ## 776      76002     1513      Ismael Rodero Monteagudo 378.25      60
    ## 777      76002      287             Luis Jaime Urbano  71.75      60
    ## 778      76002     1764          Angel Valdez Alegria 441.00      90
    ## 779      76002     1669 Juan Francisco Portillo Gomez 417.25      90
    ## 780      76002      954        Hector Aragones Frutos 238.50      30
    ## 781      76001      679 Juan Francisco Portillo Gomez 169.75      30
    ## 782      76001      267                  Hector Giron  66.75      90
    ## 783      76002      922             Luis Jaime Urbano 230.50      60
    ## 784      76002      938        Hector Aragones Frutos 234.50      90
    ## 785      76001     1822 Juan Francisco Portillo Gomez 455.50      90
    ## 786      76002      711       Fernando Mariano Berrio 177.75      60
    ## 787      76001     1829        Hector Aragones Frutos 457.25      30
    ## 788      76002      323                  Hector Giron  80.75      60
    ## 789      76001      559                  Hector Giron 139.75      60
    ## 790      76002     1847          Angel Valdez Alegria 461.75      60
    ## 791      76001     1735             Luis Jaime Urbano 433.75      30
    ## 792      76001     1811 Juan Francisco Portillo Gomez 452.75      90
    ## 793      76002     1381             Luis Jaime Urbano 345.25      30
    ## 794      76001     1879        Hector Aragones Frutos 469.75      90
    ## 795      76001     1914             Luis Jaime Urbano 478.50      60
    ## 796      76002     1490          Angel Valdez Alegria 372.50      60
    ## 797      76001      465        Hector Aragones Frutos 116.25      90
    ## 798      76002      279                  Hector Giron  69.75      30
    ## 799      76002      310             Luis Jaime Urbano  77.50      30
    ## 800      76002     1439              Felipe Villatoro 359.75      30
    ## 801      76001     1387        Hector Aragones Frutos 346.75      30
    ## 802      76002     1596             Luis Jaime Urbano 399.00      30
    ## 803      76001     1074          Pedro Alvarez Parejo 268.50      90
    ## 804      76002      505          Angel Valdez Alegria 126.25      30
    ## 805      76001     1662          Pedro Alvarez Parejo 415.50      30
    ## 806      76002      757       Fernando Mariano Berrio 189.25      90
    ## 807      76002     1991      Ismael Rodero Monteagudo 497.75      30
    ## 808      76001      231 Juan Francisco Portillo Gomez  57.75      90
    ## 809      76001      959                  Hector Giron 239.75      90
    ## 810      76001      382       Fernando Mariano Berrio  95.50      60
    ## 811      76001      736              Felipe Villatoro 184.00      90
    ## 812      76001     1734      Ismael Rodero Monteagudo 433.50      90
    ## 813      76002      584       Fernando Mariano Berrio 146.00      30
    ## 814      76001      524                  Hector Giron 131.00      90
    ## 815      76002      598                  Hector Giron 149.50      30
    ## 816      76002      851                  Hector Giron 212.75      60
    ## 817      76001     1621        Hector Aragones Frutos 405.25      30
    ## 818      76001      659          Angel Valdez Alegria 164.75      60
    ## 819      76001      810          Angel Valdez Alegria 202.50      90
    ## 820      76002      937             Luis Jaime Urbano 234.25      90
    ## 821      76001     1884      Ismael Rodero Monteagudo 471.00      60
    ## 822      76001      689 Juan Francisco Portillo Gomez 172.25      90
    ## 823      76001     1754      Ismael Rodero Monteagudo 438.50      30
    ## 824      76001     1705      Ismael Rodero Monteagudo 426.25      90
    ## 825      76002     1100      Ismael Rodero Monteagudo 275.00      60
    ## 826      76002      899          Angel Valdez Alegria 224.75      30
    ## 827      76002      953          Angel Valdez Alegria 238.25      90
    ## 828      76002     1262             Luis Jaime Urbano 315.50      60
    ## 829      76002     1496      Ismael Rodero Monteagudo 374.00      90
    ## 830      76002      810       Fernando Mariano Berrio 202.50      30
    ## 831      76002     1821       Fernando Mariano Berrio 455.25      90
    ## 832      76002      563          Angel Valdez Alegria 140.75      60
    ## 833      76001     1378 Juan Francisco Portillo Gomez 344.50      90
    ## 834      76001      561 Juan Francisco Portillo Gomez 140.25      60
    ## 835      76001     1349                  Hector Giron 337.25      30
    ## 836      76002     1047       Fernando Mariano Berrio 261.75      60
    ## 837      76001     1219              Felipe Villatoro 304.75      90
    ## 838      76001      591              Felipe Villatoro 147.75      60
    ## 839      76001      980      Ismael Rodero Monteagudo 245.00      60
    ## 840      76002      537       Fernando Mariano Berrio 134.25      60
    ## 841      76001      395 Juan Francisco Portillo Gomez  98.75      30
    ## 842      76002     1396        Hector Aragones Frutos 349.00      60
    ## 843      76002     1559        Hector Aragones Frutos 389.75      60
    ## 844      76002     1116             Luis Jaime Urbano 279.00      30
    ## 845      76002     1507        Hector Aragones Frutos 376.75      60
    ## 846      76001      752       Fernando Mariano Berrio 188.00      90
    ## 847      76001     1938                  Hector Giron 484.50      60
    ## 848      76001     1823       Fernando Mariano Berrio 455.75      90
    ## 849      76001     1740       Fernando Mariano Berrio 435.00      60
    ## 850      76001      937                  Hector Giron 234.25      90
    ## 851      76001     1842          Pedro Alvarez Parejo 460.50      90
    ## 852      76001     1090       Fernando Mariano Berrio 272.50      60
    ## 853      76002     1342      Ismael Rodero Monteagudo 335.50      60
    ## 854      76002     1618       Fernando Mariano Berrio 404.50      90
    ## 855      76001     1753          Pedro Alvarez Parejo 438.25      30
    ## 856      76001      681             Luis Jaime Urbano 170.25      30
    ## 857      76001     1908             Luis Jaime Urbano 477.00      90
    ## 858      76001      340             Luis Jaime Urbano  85.00      30
    ## 859      76001     1902       Fernando Mariano Berrio 475.50      60
    ## 860      76001     1949        Hector Aragones Frutos 487.25      30
    ## 861      76002     1583      Ismael Rodero Monteagudo 395.75      30
    ## 862      76002     1713      Ismael Rodero Monteagudo 428.25      30
    ## 863      76002     1454             Luis Jaime Urbano 363.50      60
    ## 864      76002      469       Fernando Mariano Berrio 117.25      60
    ## 865      76001      620              Felipe Villatoro 155.00      90
    ## 866      76001     1169       Fernando Mariano Berrio 292.25      30
    ## 867      76001     1619        Hector Aragones Frutos 404.75      30
    ## 868      76001      880 Juan Francisco Portillo Gomez 220.00      30
    ## 869      76001     1623          Pedro Alvarez Parejo 405.75      90
    ## 870      76002     1079        Hector Aragones Frutos 269.75      60
    ## 871      76002      582              Felipe Villatoro 145.50      60
    ## 872      76002     1882       Fernando Mariano Berrio 470.50      60
    ## 873      76001     1330             Luis Jaime Urbano 332.50      60
    ## 874      76002      751        Hector Aragones Frutos 187.75      90
    ## 875      76001     1697 Juan Francisco Portillo Gomez 424.25      30
    ## 876      76002     1261 Juan Francisco Portillo Gomez 315.25      60
    ## 877      76001     1722             Luis Jaime Urbano 430.50      30
    ## 878      76001      639      Ismael Rodero Monteagudo 159.75      60
    ## 879      76001      504        Hector Aragones Frutos 126.00      60
    ## 880      76001     1400             Luis Jaime Urbano 350.00      30
    ## 881      76001     1132      Ismael Rodero Monteagudo 283.00      60
    ## 882      76002      331             Luis Jaime Urbano  82.75      60
    ## 883      76002     1064      Ismael Rodero Monteagudo 266.00      30
    ## 884      76002     1455       Fernando Mariano Berrio 363.75      30
    ## 885      76002      925          Angel Valdez Alegria 231.25      30
    ## 886      76002      683          Pedro Alvarez Parejo 170.75      60
    ## 887      76001      370 Juan Francisco Portillo Gomez  92.50      30
    ## 888      76002      510              Felipe Villatoro 127.50      30
    ## 889      76001      875       Fernando Mariano Berrio 218.75      60
    ## 890      76002      271                  Hector Giron  67.75      60
    ## 891      76001     1522              Felipe Villatoro 380.50      30
    ## 892      76002     1082             Luis Jaime Urbano 270.50      30
    ## 893      76002      966          Angel Valdez Alegria 241.50      90
    ## 894      76001     1150          Angel Valdez Alegria 287.50      30
    ## 895      76001     1887              Felipe Villatoro 471.75      90
    ## 896      76001      714              Felipe Villatoro 178.50      90
    ## 897      76002     1340        Hector Aragones Frutos 335.00      30
    ## 898      76001     1289                  Hector Giron 322.25      60
    ## 899      76002      807          Pedro Alvarez Parejo 201.75      60
    ## 900      76002     1833        Hector Aragones Frutos 458.25      90
    ## 901      76001     1301       Fernando Mariano Berrio 325.25      60
    ## 902      76002      651          Pedro Alvarez Parejo 162.75      60
    ## 903      76002      225          Pedro Alvarez Parejo  56.25      90
    ## 904      76002      935 Juan Francisco Portillo Gomez 233.75      90
    ## 905      76001      840                  Hector Giron 210.00      60
    ## 906      76002      820             Luis Jaime Urbano 205.00      90
    ## 907      76002      587 Juan Francisco Portillo Gomez 146.75      30
    ## 908      76002      581             Luis Jaime Urbano 145.25      60
    ## 909      76002     1769             Luis Jaime Urbano 442.25      30
    ## 910      76002      847       Fernando Mariano Berrio 211.75      30
    ## 911      76001     1168      Ismael Rodero Monteagudo 292.00      60
    ## 912      76001     1760 Juan Francisco Portillo Gomez 440.00      90
    ## 913      76002     1877                  Hector Giron 469.25      60
    ## 914      76001     1132       Fernando Mariano Berrio 283.00      90
    ## 915      76001     1187             Luis Jaime Urbano 296.75      90
    ## 916      76002      472              Felipe Villatoro 118.00      30
    ## 917      76001     1774      Ismael Rodero Monteagudo 443.50      60
    ## 918      76002      362                  Hector Giron  90.50      60
    ## 919      76001     1310              Felipe Villatoro 327.50      60
    ## 920      76002      885              Felipe Villatoro 221.25      60
    ## 921      76001     1920 Juan Francisco Portillo Gomez 480.00      30
    ## 922      76002      319              Felipe Villatoro  79.75      30
    ## 923      76002      202        Hector Aragones Frutos  50.50      60
    ## 924      76002      504             Luis Jaime Urbano 126.00      30
    ## 925      76002     1167      Ismael Rodero Monteagudo 291.75      30
    ## 926      76001     1755      Ismael Rodero Monteagudo 438.75      60
    ## 927      76002      489        Hector Aragones Frutos 122.25      90
    ## 928      76001      299          Angel Valdez Alegria  74.75      60
    ## 929      76002     1754                  Hector Giron 438.50      90
    ## 930      76002      810 Juan Francisco Portillo Gomez 202.50      30
    ## 931      76001     1805      Ismael Rodero Monteagudo 451.25      90
    ## 932      76001     1980       Fernando Mariano Berrio 495.00      90
    ## 933      76002      942              Felipe Villatoro 235.50      30
    ## 934      76001     1810       Fernando Mariano Berrio 452.50      90
    ## 935      76001      916          Angel Valdez Alegria 229.00      60
    ## 936      76002      681                  Hector Giron 170.25      30
    ## 937      76001     1028          Pedro Alvarez Parejo 257.00      90
    ## 938      76001     1818          Pedro Alvarez Parejo 454.50      90
    ## 939      76001      813        Hector Aragones Frutos 203.25      30
    ## 940      76002      575          Angel Valdez Alegria 143.75      60
    ## 941      76001     1296                  Hector Giron 324.00      60
    ## 942      76001     1023          Pedro Alvarez Parejo 255.75      30
    ## 943      76001     1333             Luis Jaime Urbano 333.25      90
    ## 944      76001      560 Juan Francisco Portillo Gomez 140.00      60
    ## 945      76002      719                  Hector Giron 179.75      60
    ## 946      76002     1442       Fernando Mariano Berrio 360.50      60
    ## 947      76001     1430       Fernando Mariano Berrio 357.50      60
    ## 948      76001     1201        Hector Aragones Frutos 300.25      60
    ## 949      76001     1212 Juan Francisco Portillo Gomez 303.00      30
    ## 950      76001      310             Luis Jaime Urbano  77.50      60
    ## 951      76001     1057          Pedro Alvarez Parejo 264.25      90
    ## 952      76001      971          Angel Valdez Alegria 242.75      60
    ## 953      76001     1006          Pedro Alvarez Parejo 251.50      30
    ## 954      76001     1005 Juan Francisco Portillo Gomez 251.25      30
    ## 955      76002      470 Juan Francisco Portillo Gomez 117.50      60
    ## 956      76001     1641                  Hector Giron 410.25      90
    ## 957      76002      890          Angel Valdez Alegria 222.50      60
    ## 958      76002     1392       Fernando Mariano Berrio 348.00      90
    ## 959      76002     1317          Pedro Alvarez Parejo 329.25      30
    ## 960      76002     1802        Hector Aragones Frutos 450.50      30
    ## 961      76002      870       Fernando Mariano Berrio 217.50      90
    ## 962      76002     1497          Angel Valdez Alegria 374.25      30
    ## 963      76002      736                  Hector Giron 184.00      60
    ## 964      76002      767             Luis Jaime Urbano 191.75      60
    ## 965      76001     1371          Angel Valdez Alegria 342.75      90
    ## 966      76002     1211          Angel Valdez Alegria 302.75      30
    ## 967      76002     1816 Juan Francisco Portillo Gomez 454.00      90
    ## 968      76002     1726       Fernando Mariano Berrio 431.50      90
    ## 969      76001      801          Angel Valdez Alegria 200.25      90
    ## 970      76001     1512 Juan Francisco Portillo Gomez 378.00      30
    ## 971      76002      633                  Hector Giron 158.25      60
    ## 972      76002      933          Pedro Alvarez Parejo 233.25      60
    ## 973      76001     1657       Fernando Mariano Berrio 414.25      30
    ## 974      76001      234          Angel Valdez Alegria  58.50      90
    ## 975      76002      203             Luis Jaime Urbano  50.75      30
    ## 976      76001     1848          Angel Valdez Alegria 462.00      30
    ## 977      76001     1307        Hector Aragones Frutos 326.75      60
    ## 978      76001     1139        Hector Aragones Frutos 284.75      90
    ## 979      76002      784       Fernando Mariano Berrio 196.00      60
    ## 980      76002     1825             Luis Jaime Urbano 456.25      60
    ## 981      76002      682              Felipe Villatoro 170.50      60
    ## 982      76002      735             Luis Jaime Urbano 183.75      60
    ## 983      76001     1062              Felipe Villatoro 265.50      60
    ## 984      76001     1733              Felipe Villatoro 433.25      90
    ## 985      76002     1483                  Hector Giron 370.75      30
    ## 986      76002     1311                  Hector Giron 327.75      60
    ## 987      76001      933        Hector Aragones Frutos 233.25      60
    ## 988      76002     1838             Luis Jaime Urbano 459.50      90
    ## 989      76002     1325          Pedro Alvarez Parejo 331.25      30
    ## 990      76001      497                  Hector Giron 124.25      60
    ## 991      76002     1177       Fernando Mariano Berrio 294.25      60
    ## 992      76002     1872      Ismael Rodero Monteagudo 468.00      90
    ## 993      76002     1663                  Hector Giron 415.75      90
    ## 994      76001     1657          Pedro Alvarez Parejo 414.25      90
    ## 995      76002      457          Angel Valdez Alegria 114.25      60
    ## 996      76001     1574              Felipe Villatoro 393.50      30
    ## 997      76002      904        Hector Aragones Frutos 226.00      30
    ## 998      76001     1939        Hector Aragones Frutos 484.75      90
    ## 999      76001     1852             Luis Jaime Urbano 463.00      60
    ## 1000     76001     1909        Hector Aragones Frutos 477.25      90
    ## 1001     76001     1411              Felipe Villatoro 352.75      90
    ## 1002     76002      398       Fernando Mariano Berrio  99.50      60
    ## 1003     76001      251        Hector Aragones Frutos  62.75      60
    ## 1004     76001      235        Hector Aragones Frutos  58.75      90
    ## 1005     76002     1026              Felipe Villatoro 256.50      60
    ## 1006     76002     1221                  Hector Giron 305.25      90
    ## 1007     76001      313          Angel Valdez Alegria  78.25      90
    ## 1008     76001     1474                  Hector Giron 368.50      30
    ## 1009     76002     1194                  Hector Giron 298.50      60
    ## 1010     76001     1147        Hector Aragones Frutos 286.75      60
    ## 1011     76001      439          Pedro Alvarez Parejo 109.75      60
    ## 1012     76001     1748       Fernando Mariano Berrio 437.00      60
    ## 1013     76001      577      Ismael Rodero Monteagudo 144.25      60
    ## 1014     76002     1550        Hector Aragones Frutos 387.50      60
    ## 1015     76002      319 Juan Francisco Portillo Gomez  79.75      90
    ## 1016     76001      960                  Hector Giron 240.00      90
    ## 1017     76001      264          Pedro Alvarez Parejo  66.00      90
    ## 1018     76001      859              Felipe Villatoro 214.75      30
    ## 1019     76002     1210                  Hector Giron 302.50      60
    ## 1020     76002     1592          Angel Valdez Alegria 398.00      30
    ## 1021     76002     1186              Felipe Villatoro 296.50      30
    ## 1022     76001     1763          Angel Valdez Alegria 440.75      60
    ## 1023     76002      217              Felipe Villatoro  54.25      60
    ## 1024     76002     1783      Ismael Rodero Monteagudo 445.75      90
    ## 1025     76002      805      Ismael Rodero Monteagudo 201.25      90
    ## 1026     76001     1241          Angel Valdez Alegria 310.25      30
    ## 1027     76002     1760                  Hector Giron 440.00      30
    ## 1028     76002     1915 Juan Francisco Portillo Gomez 478.75      60
    ## 1029     76001     1798             Luis Jaime Urbano 449.50      30
    ## 1030     76002     1327       Fernando Mariano Berrio 331.75      30
    ## 1031     76001     1167       Fernando Mariano Berrio 291.75      30
    ## 1032     76002     1256      Ismael Rodero Monteagudo 314.00      60
    ## 1033     76001     1290 Juan Francisco Portillo Gomez 322.50      60
    ## 1034     76002      511       Fernando Mariano Berrio 127.75      90
    ## 1035     76002      287        Hector Aragones Frutos  71.75      90
    ## 1036     76001     1318             Luis Jaime Urbano 329.50      60
    ## 1037     76002      906          Pedro Alvarez Parejo 226.50      60
    ## 1038     76002     1921          Angel Valdez Alegria 480.25      90
    ## 1039     76001     1279          Pedro Alvarez Parejo 319.75      30
    ## 1040     76001      445      Ismael Rodero Monteagudo 111.25      60
    ## 1041     76002     1616       Fernando Mariano Berrio 404.00      30
    ## 1042     76001      868                  Hector Giron 217.00      30
    ## 1043     76002      789          Pedro Alvarez Parejo 197.25      30
    ## 1044     76001      547             Luis Jaime Urbano 136.75      90
    ## 1045     76002      700              Felipe Villatoro 175.00      90
    ## 1046     76002     1377      Ismael Rodero Monteagudo 344.25      30
    ## 1047     76001     1326          Angel Valdez Alegria 331.50      60
    ## 1048     76002      322 Juan Francisco Portillo Gomez  80.50      60
    ## 1049     76001      223             Luis Jaime Urbano  55.75      60
    ## 1050     76001     1767             Luis Jaime Urbano 441.75      90
    ## 1051     76001     1048                  Hector Giron 262.00      90
    ## 1052     76001     1114          Angel Valdez Alegria 278.50      60
    ## 1053     76002      740              Felipe Villatoro 185.00      90
    ## 1054     76002      776          Angel Valdez Alegria 194.00      60
    ## 1055     76002      609              Felipe Villatoro 152.25      60
    ## 1056     76002     1660             Luis Jaime Urbano 415.00      30
    ## 1057     76001      272             Luis Jaime Urbano  68.00      60
    ## 1058     76001      526       Fernando Mariano Berrio 131.50      90
    ## 1059     76002      598          Angel Valdez Alegria 149.50      90
    ## 1060     76002      747        Hector Aragones Frutos 186.75      90
    ## 1061     76002     1351              Felipe Villatoro 337.75      90
    ## 1062     76001     1515          Angel Valdez Alegria 378.75      60
    ## 1063     76002     1499          Pedro Alvarez Parejo 374.75      30
    ## 1064     76002     1757          Angel Valdez Alegria 439.25      90
    ## 1065     76001     1613      Ismael Rodero Monteagudo 403.25      30
    ## 1066     76001     1928          Pedro Alvarez Parejo 482.00      30
    ## 1067     76002     1124          Angel Valdez Alegria 281.00      30
    ## 1068     76002     1052             Luis Jaime Urbano 263.00      30
    ## 1069     76001     1035             Luis Jaime Urbano 258.75      90
    ## 1070     76001     1275             Luis Jaime Urbano 318.75      90
    ## 1071     76002      323      Ismael Rodero Monteagudo  80.75      30
    ## 1072     76002     1496             Luis Jaime Urbano 374.00      60
    ## 1073     76002      771        Hector Aragones Frutos 192.75      30
    ## 1074     76002     1625      Ismael Rodero Monteagudo 406.25      90
    ## 1075     76001     1252             Luis Jaime Urbano 313.00      60
    ## 1076     76002     1199       Fernando Mariano Berrio 299.75      60
    ## 1077     76002     1889                  Hector Giron 472.25      90
    ## 1078     76002     1051 Juan Francisco Portillo Gomez 262.75      90
    ## 1079     76002      595                  Hector Giron 148.75      30
    ## 1080     76002      965                  Hector Giron 241.25      30
    ## 1081     76002     1615          Angel Valdez Alegria 403.75      60
    ## 1082     76002      296        Hector Aragones Frutos  74.00      30
    ## 1083     76001     1784       Fernando Mariano Berrio 446.00      90
    ## 1084     76002      386              Felipe Villatoro  96.50      60
    ## 1085     76001     1176             Luis Jaime Urbano 294.00      90
    ## 1086     76001      259      Ismael Rodero Monteagudo  64.75      90
    ## 1087     76002      443 Juan Francisco Portillo Gomez 110.75      90
    ## 1088     76002      917       Fernando Mariano Berrio 229.25      90
    ## 1089     76001      917 Juan Francisco Portillo Gomez 229.25      90
    ## 1090     76001      406          Pedro Alvarez Parejo 101.50      90
    ## 1091     76002     1674       Fernando Mariano Berrio 418.50      60
    ## 1092     76002      546              Felipe Villatoro 136.50      30
    ## 1093     76001     1263                  Hector Giron 315.75      60
    ## 1094     76001      509 Juan Francisco Portillo Gomez 127.25      90
    ## 1095     76001     1840          Pedro Alvarez Parejo 460.00      30
    ## 1096     76001     1472             Luis Jaime Urbano 368.00      30
    ## 1097     76002      242          Pedro Alvarez Parejo  60.50      30
    ## 1098     76001      880      Ismael Rodero Monteagudo 220.00      90
    ## 1099     76002     1028        Hector Aragones Frutos 257.00      30
    ## 1100     76002     1830          Pedro Alvarez Parejo 457.50      30
    ## 1101     76001      597                  Hector Giron 149.25      60
    ## 1102     76001     1755        Hector Aragones Frutos 438.75      30
    ## 1103     76002      608             Luis Jaime Urbano 152.00      90
    ## 1104     76002      883       Fernando Mariano Berrio 220.75      30
    ## 1105     76001      677        Hector Aragones Frutos 169.25      60
    ## 1106     76001     1554       Fernando Mariano Berrio 388.50      30
    ## 1107     76001     1004          Pedro Alvarez Parejo 251.00      60
    ## 1108     76001      540                  Hector Giron 135.00      60
    ## 1109     76001     1936                  Hector Giron 484.00      30
    ## 1110     76002     1227              Felipe Villatoro 306.75      30
    ## 1111     76001     1266                  Hector Giron 316.50      60
    ## 1112     76002     1291              Felipe Villatoro 322.75      60
    ## 1113     76002     1470        Hector Aragones Frutos 367.50      60
    ## 1114     76002     1029             Luis Jaime Urbano 257.25      30
    ## 1115     76002      614             Luis Jaime Urbano 153.50      30
    ## 1116     76002      809          Pedro Alvarez Parejo 202.25      60
    ## 1117     76001      986                  Hector Giron 246.50      90
    ## 1118     76002     1573              Felipe Villatoro 393.25      60
    ## 1119     76002      227        Hector Aragones Frutos  56.75      60
    ## 1120     76002      723                  Hector Giron 180.75      60
    ## 1121     76002      351        Hector Aragones Frutos  87.75      60
    ## 1122     76002     1865                  Hector Giron 466.25      60
    ## 1123     76001     1480             Luis Jaime Urbano 370.00      60
    ## 1124     76002     1206              Felipe Villatoro 301.50      90
    ## 1125     76001      576      Ismael Rodero Monteagudo 144.00      90
    ## 1126     76002     1273      Ismael Rodero Monteagudo 318.25      30
    ## 1127     76001     1598      Ismael Rodero Monteagudo 399.50      30
    ## 1128     76001      318      Ismael Rodero Monteagudo  79.50      60
    ## 1129     76001      381             Luis Jaime Urbano  95.25      30
    ## 1130     76002     1342 Juan Francisco Portillo Gomez 335.50      90
    ## 1131     76002     1985          Pedro Alvarez Parejo 496.25      90
    ## 1132     76001      273             Luis Jaime Urbano  68.25      60
    ## 1133     76001     1008      Ismael Rodero Monteagudo 252.00      60
    ## 1134     76002      633      Ismael Rodero Monteagudo 158.25      30
    ## 1135     76001     1694 Juan Francisco Portillo Gomez 423.50      30
    ## 1136     76001      359              Felipe Villatoro  89.75      30
    ## 1137     76002      282          Angel Valdez Alegria  70.50      60
    ## 1138     76002      266       Fernando Mariano Berrio  66.50      30
    ## 1139     76002     1095          Pedro Alvarez Parejo 273.75      90
    ## 1140     76001     1468      Ismael Rodero Monteagudo 367.00      30
    ## 1141     76002      370       Fernando Mariano Berrio  92.50      30
    ## 1142     76001     1561      Ismael Rodero Monteagudo 390.25      30
    ## 1143     76001      918      Ismael Rodero Monteagudo 229.50      30
    ## 1144     76001     1771             Luis Jaime Urbano 442.75      30
    ## 1145     76001     1872        Hector Aragones Frutos 468.00      90
    ## 1146     76001      860                  Hector Giron 215.00      60
    ## 1147     76001     1270          Angel Valdez Alegria 317.50      60
    ## 1148     76002     1260        Hector Aragones Frutos 315.00      90
    ## 1149     76002     1762             Luis Jaime Urbano 440.50      90
    ## 1150     76002     1680        Hector Aragones Frutos 420.00      30
    ## 1151     76001      973        Hector Aragones Frutos 243.25      90
    ## 1152     76002     1060       Fernando Mariano Berrio 265.00      60
    ## 1153     76001      831             Luis Jaime Urbano 207.75      30
    ## 1154     76001      864                  Hector Giron 216.00      90
    ## 1155     76001     1564              Felipe Villatoro 391.00      30
    ## 1156     76001      210             Luis Jaime Urbano  52.50      60
    ## 1157     76001      474          Angel Valdez Alegria 118.50      90
    ## 1158     76001     1484          Pedro Alvarez Parejo 371.00      30
    ## 1159     76002      668             Luis Jaime Urbano 167.00      60
    ## 1160     76001      949                  Hector Giron 237.25      30
    ## 1161     76002     1057        Hector Aragones Frutos 264.25      30
    ## 1162     76001      558 Juan Francisco Portillo Gomez 139.50      60
    ## 1163     76001      237                  Hector Giron  59.25      90
    ## 1164     76002      549       Fernando Mariano Berrio 137.25      60
    ## 1165     76001      530             Luis Jaime Urbano 132.50      60
    ## 1166     76002      453              Felipe Villatoro 113.25      90
    ## 1167     76001      616       Fernando Mariano Berrio 154.00      60
    ## 1168     76001     1973        Hector Aragones Frutos 493.25      30
    ## 1169     76001      862          Angel Valdez Alegria 215.50      60
    ## 1170     76001     1641          Angel Valdez Alegria 410.25      90
    ## 1171     76001     1795              Felipe Villatoro 448.75      90
    ## 1172     76002     1951             Luis Jaime Urbano 487.75      60
    ## 1173     76001      358      Ismael Rodero Monteagudo  89.50      60
    ## 1174     76002      426          Pedro Alvarez Parejo 106.50      30
    ## 1175     76002     1330 Juan Francisco Portillo Gomez 332.50      90
    ## 1176     76001     1595      Ismael Rodero Monteagudo 398.75      90
    ## 1177     76002      294          Angel Valdez Alegria  73.50      90
    ## 1178     76002      668 Juan Francisco Portillo Gomez 167.00      30
    ## 1179     76002      256 Juan Francisco Portillo Gomez  64.00      30
    ## 1180     76001     1959              Felipe Villatoro 489.75      30
    ## 1181     76001     1970       Fernando Mariano Berrio 492.50      30
    ## 1182     76001     1367        Hector Aragones Frutos 341.75      90
    ## 1183     76002     1391          Angel Valdez Alegria 347.75      60
    ## 1184     76001      344          Pedro Alvarez Parejo  86.00      60
    ## 1185     76001      633              Felipe Villatoro 158.25      30
    ## 1186     76001     1085       Fernando Mariano Berrio 271.25      60
    ## 1187     76001     1212          Angel Valdez Alegria 303.00      60
    ## 1188     76002      899        Hector Aragones Frutos 224.75      30
    ## 1189     76001     1562       Fernando Mariano Berrio 390.50      30
    ## 1190     76002     1113          Angel Valdez Alegria 278.25      30
    ## 1191     76002      446          Pedro Alvarez Parejo 111.50      30
    ## 1192     76002     1517             Luis Jaime Urbano 379.25      90
    ## 1193     76002      570                  Hector Giron 142.50      60
    ## 1194     76002     1619          Pedro Alvarez Parejo 404.75      60
    ## 1195     76001      213      Ismael Rodero Monteagudo  53.25      30
    ## 1196     76001      318      Ismael Rodero Monteagudo  79.50      30
    ## 1197     76002      956          Angel Valdez Alegria 239.00      30
    ## 1198     76002      948                  Hector Giron 237.00      30
    ## 1199     76001      447 Juan Francisco Portillo Gomez 111.75      60
    ## 1200     76001     1752              Felipe Villatoro 438.00      60
    ## 1201     76001      247              Felipe Villatoro  61.75      30
    ## 1202     76001      627          Angel Valdez Alegria 156.75      90
    ## 1203     76002     1334          Angel Valdez Alegria 333.50      90
    ## 1204     76002     1297                  Hector Giron 324.25      30
    ## 1205     76001      518          Angel Valdez Alegria 129.50      30
    ## 1206     76002     1162 Juan Francisco Portillo Gomez 290.50      90
    ## 1207     76002     1088          Pedro Alvarez Parejo 272.00      30
    ## 1208     76001      994       Fernando Mariano Berrio 248.50      90
    ## 1209     76002     1368              Felipe Villatoro 342.00      90
    ## 1210     76002     1839              Felipe Villatoro 459.75      30
    ## 1211     76002     1574              Felipe Villatoro 393.50      30
    ## 1212     76002      259          Angel Valdez Alegria  64.75      60
    ## 1213     76001      267      Ismael Rodero Monteagudo  66.75      30
    ## 1214     76001     1794        Hector Aragones Frutos 448.50      30
    ## 1215     76001      855          Pedro Alvarez Parejo 213.75      60
    ## 1216     76001     1322      Ismael Rodero Monteagudo 330.50      60
    ## 1217     76001     1696                  Hector Giron 424.00      60
    ## 1218     76002     1532      Ismael Rodero Monteagudo 383.00      30
    ## 1219     76001     1769       Fernando Mariano Berrio 442.25      90
    ## 1220     76002     1864              Felipe Villatoro 466.00      30
    ## 1221     76001      225                  Hector Giron  56.25      60
    ## 1222     76002     1434             Luis Jaime Urbano 358.50      30
    ## 1223     76002      836             Luis Jaime Urbano 209.00      90
    ## 1224     76001     1703             Luis Jaime Urbano 425.75      90
    ## 1225     76001     1369 Juan Francisco Portillo Gomez 342.25      30
    ## 1226     76002     1577      Ismael Rodero Monteagudo 394.25      60
    ## 1227     76002      778        Hector Aragones Frutos 194.50      30
    ## 1228     76001     1451 Juan Francisco Portillo Gomez 362.75      60
    ## 1229     76001      784          Pedro Alvarez Parejo 196.00      90
    ## 1230     76001      206      Ismael Rodero Monteagudo  51.50      30
    ## 1231     76002      269       Fernando Mariano Berrio  67.25      30
    ## 1232     76002      562          Pedro Alvarez Parejo 140.50      30
    ## 1233     76001     1251       Fernando Mariano Berrio 312.75      60
    ## 1234     76001     1031 Juan Francisco Portillo Gomez 257.75      90
    ## 1235     76001      663      Ismael Rodero Monteagudo 165.75      60
    ## 1236     76002     1852 Juan Francisco Portillo Gomez 463.00      30
    ## 1237     76001      847       Fernando Mariano Berrio 211.75      30
    ## 1238     76002     1144          Pedro Alvarez Parejo 286.00      30
    ## 1239     76002     1564             Luis Jaime Urbano 391.00      30
    ## 1240     76002     1349              Felipe Villatoro 337.25      60
    ## 1241     76001      467                  Hector Giron 116.75      60
    ## 1242     76001     1353          Angel Valdez Alegria 338.25      90
    ## 1243     76001     1122 Juan Francisco Portillo Gomez 280.50      90
    ## 1244     76001      357 Juan Francisco Portillo Gomez  89.25      30
    ## 1245     76002      921                  Hector Giron 230.25      90
    ## 1246     76001      520              Felipe Villatoro 130.00      30
    ## 1247     76002     1144      Ismael Rodero Monteagudo 286.00      30
    ## 1248     76002      808       Fernando Mariano Berrio 202.00      30
    ## 1249     76001     1627             Luis Jaime Urbano 406.75      60
    ## 1250     76001      665        Hector Aragones Frutos 166.25      90
    ## 1251     76002     1793              Felipe Villatoro 448.25      30
    ## 1252     76002     1393                  Hector Giron 348.25      30
    ## 1253     76001      625 Juan Francisco Portillo Gomez 156.25      90
    ## 1254     76002     1063              Felipe Villatoro 265.75      30
    ## 1255     76001     1461      Ismael Rodero Monteagudo 365.25      30
    ## 1256     76001     1564          Pedro Alvarez Parejo 391.00      30
    ## 1257     76002     1309       Fernando Mariano Berrio 327.25      30
    ## 1258     76001     1475       Fernando Mariano Berrio 368.75      90
    ## 1259     76001      581          Angel Valdez Alegria 145.25      60
    ## 1260     76002     1787          Pedro Alvarez Parejo 446.75      90
    ## 1261     76002     1363                  Hector Giron 340.75      30
    ## 1262     76001     1550                  Hector Giron 387.50      90
    ## 1263     76002     1408                  Hector Giron 352.00      60
    ## 1264     76002      725 Juan Francisco Portillo Gomez 181.25      30
    ## 1265     76001     1452        Hector Aragones Frutos 363.00      90
    ## 1266     76002     1080             Luis Jaime Urbano 270.00      60
    ## 1267     76002     1919        Hector Aragones Frutos 479.75      30
    ## 1268     76002     1205        Hector Aragones Frutos 301.25      60
    ## 1269     76001     1917       Fernando Mariano Berrio 479.25      90
    ## 1270     76002     1852              Felipe Villatoro 463.00      90
    ## 1271     76002     1690          Pedro Alvarez Parejo 422.50      30
    ## 1272     76002      725        Hector Aragones Frutos 181.25      60
    ## 1273     76002      260                  Hector Giron  65.00      90
    ## 1274     76002     1330                  Hector Giron 332.50      90
    ## 1275     76002      439              Felipe Villatoro 109.75      60
    ## 1276     76001      390      Ismael Rodero Monteagudo  97.50      90
    ## 1277     76001     1605       Fernando Mariano Berrio 401.25      90
    ## 1278     76001     1785              Felipe Villatoro 446.25      60
    ## 1279     76001     1321              Felipe Villatoro 330.25      90
    ## 1280     76002      455          Pedro Alvarez Parejo 113.75      90
    ## 1281     76002      400 Juan Francisco Portillo Gomez 100.00      60
    ## 1282     76002     1536       Fernando Mariano Berrio 384.00      60
    ## 1283     76002     1506              Felipe Villatoro 376.50      60
    ## 1284     76002     1444          Pedro Alvarez Parejo 361.00      60
    ## 1285     76001     1336       Fernando Mariano Berrio 334.00      30
    ## 1286     76001     1114 Juan Francisco Portillo Gomez 278.50      60
    ## 1287     76001      417              Felipe Villatoro 104.25      90
    ## 1288     76002     1460      Ismael Rodero Monteagudo 365.00      60
    ## 1289     76001     1444        Hector Aragones Frutos 361.00      30
    ## 1290     76001     1985        Hector Aragones Frutos 496.25      60
    ## 1291     76001      474        Hector Aragones Frutos 118.50      30
    ## 1292     76002      528              Felipe Villatoro 132.00      60
    ## 1293     76001     1295       Fernando Mariano Berrio 323.75      30
    ## 1294     76002      735          Pedro Alvarez Parejo 183.75      30
    ## 1295     76001     1207 Juan Francisco Portillo Gomez 301.75      30
    ## 1296     76002     1840      Ismael Rodero Monteagudo 460.00      60
    ## 1297     76002      217        Hector Aragones Frutos  54.25      60
    ## 1298     76001     1568          Pedro Alvarez Parejo 392.00      90
    ## 1299     76002      540      Ismael Rodero Monteagudo 135.00      60
    ## 1300     76002     1292 Juan Francisco Portillo Gomez 323.00      90
    ## 1301     76002     1445          Angel Valdez Alegria 361.25      60
    ## 1302     76002     1083              Felipe Villatoro 270.75      30
    ## 1303     76002     1290      Ismael Rodero Monteagudo 322.50      30
    ## 1304     76001     1479          Angel Valdez Alegria 369.75      60
    ## 1305     76001      867        Hector Aragones Frutos 216.75      30
    ## 1306     76001      673      Ismael Rodero Monteagudo 168.25      60
    ## 1307     76001      658             Luis Jaime Urbano 164.50      30
    ## 1308     76002     1673       Fernando Mariano Berrio 418.25      60
    ## 1309     76001     1462      Ismael Rodero Monteagudo 365.50      60
    ## 1310     76001     1333      Ismael Rodero Monteagudo 333.25      30
    ## 1311     76002      593          Pedro Alvarez Parejo 148.25      90
    ## 1312     76001      223 Juan Francisco Portillo Gomez  55.75      30
    ## 1313     76001     1486 Juan Francisco Portillo Gomez 371.50      60
    ## 1314     76001     1684      Ismael Rodero Monteagudo 421.00      30
    ## 1315     76001     1957       Fernando Mariano Berrio 489.25      60
    ## 1316     76002      221      Ismael Rodero Monteagudo  55.25      60
    ## 1317     76001      604             Luis Jaime Urbano 151.00      60
    ## 1318     76001     1619          Angel Valdez Alegria 404.75      60
    ## 1319     76002      355          Pedro Alvarez Parejo  88.75      60
    ## 1320     76002     1524          Pedro Alvarez Parejo 381.00      90
    ## 1321     76002     1178        Hector Aragones Frutos 294.50      30
    ## 1322     76002     1174          Pedro Alvarez Parejo 293.50      90
    ## 1323     76001      645              Felipe Villatoro 161.25      90
    ## 1324     76002     1368              Felipe Villatoro 342.00      90
    ## 1325     76002      652                  Hector Giron 163.00      30
    ## 1326     76002      866 Juan Francisco Portillo Gomez 216.50      30
    ## 1327     76001     1337          Pedro Alvarez Parejo 334.25      90
    ## 1328     76002      570              Felipe Villatoro 142.50      60
    ## 1329     76002      484 Juan Francisco Portillo Gomez 121.00      60
    ## 1330     76001     1858          Angel Valdez Alegria 464.50      60
    ## 1331     76002     1427       Fernando Mariano Berrio 356.75      90
    ## 1332     76001     1920             Luis Jaime Urbano 480.00      30
    ## 1333     76002     1183      Ismael Rodero Monteagudo 295.75      30
    ## 1334     76002     1536          Angel Valdez Alegria 384.00      90
    ## 1335     76001     1063          Angel Valdez Alegria 265.75      30
    ## 1336     76002     1981             Luis Jaime Urbano 495.25      60
    ## 1337     76002      298        Hector Aragones Frutos  74.50      30
    ## 1338     76002      356             Luis Jaime Urbano  89.00      90
    ## 1339     76002      915      Ismael Rodero Monteagudo 228.75      60
    ## 1340     76001      214      Ismael Rodero Monteagudo  53.50      60
    ## 1341     76002     1811          Angel Valdez Alegria 452.75      30
    ## 1342     76001     1349      Ismael Rodero Monteagudo 337.25      60
    ## 1343     76002      652          Pedro Alvarez Parejo 163.00      30
    ## 1344     76002      437             Luis Jaime Urbano 109.25      60
    ## 1345     76002      583 Juan Francisco Portillo Gomez 145.75      60
    ## 1346     76001     1818                  Hector Giron 454.50      30
    ## 1347     76001     1811             Luis Jaime Urbano 452.75      60
    ## 1348     76002     1938       Fernando Mariano Berrio 484.50      90
    ## 1349     76001     1930      Ismael Rodero Monteagudo 482.50      60
    ## 1350     76001      907       Fernando Mariano Berrio 226.75      60
    ## 1351     76001      212        Hector Aragones Frutos  53.00      30
    ## 1352     76002     1387             Luis Jaime Urbano 346.75      90
    ## 1353     76002      316                  Hector Giron  79.00      90
    ## 1354     76002      218                  Hector Giron  54.50      60
    ## 1355     76001      565                  Hector Giron 141.25      60
    ## 1356     76001      893        Hector Aragones Frutos 223.25      90
    ## 1357     76001      595              Felipe Villatoro 148.75      30
    ## 1358     76002     1303             Luis Jaime Urbano 325.75      60
    ## 1359     76002      303 Juan Francisco Portillo Gomez  75.75      90
    ## 1360     76002      703        Hector Aragones Frutos 175.75      30
    ## 1361     76002     1149                  Hector Giron 287.25      60
    ## 1362     76002      996          Pedro Alvarez Parejo 249.00      60
    ## 1363     76001     1107        Hector Aragones Frutos 276.75      90
    ## 1364     76001     1668              Felipe Villatoro 417.00      90
    ## 1365     76001     1196              Felipe Villatoro 299.00      30
    ## 1366     76001     1863 Juan Francisco Portillo Gomez 465.75      30
    ## 1367     76001     1980          Angel Valdez Alegria 495.00      30
    ## 1368     76001      419                  Hector Giron 104.75      90
    ## 1369     76002     1269          Angel Valdez Alegria 317.25      60
    ## 1370     76002      304        Hector Aragones Frutos  76.00      90
    ## 1371     76002      625          Pedro Alvarez Parejo 156.25      90
    ## 1372     76001     1073       Fernando Mariano Berrio 268.25      90
    ## 1373     76001      541        Hector Aragones Frutos 135.25      90
    ## 1374     76002      363              Felipe Villatoro  90.75      60
    ## 1375     76001      314 Juan Francisco Portillo Gomez  78.50      30
    ## 1376     76001      304       Fernando Mariano Berrio  76.00      30
    ## 1377     76001     1151             Luis Jaime Urbano 287.75      30
    ## 1378     76002     1050      Ismael Rodero Monteagudo 262.50      60
    ## 1379     76002     1723                  Hector Giron 430.75      60
    ## 1380     76002     1305          Angel Valdez Alegria 326.25      60
    ## 1381     76001      422        Hector Aragones Frutos 105.50      30
    ## 1382     76001     1641      Ismael Rodero Monteagudo 410.25      60
    ## 1383     76001      386      Ismael Rodero Monteagudo  96.50      60
    ## 1384     76001     1079          Pedro Alvarez Parejo 269.75      60
    ## 1385     76001      703      Ismael Rodero Monteagudo 175.75      30
    ## 1386     76002      648      Ismael Rodero Monteagudo 162.00      30
    ## 1387     76002     1730       Fernando Mariano Berrio 432.50      30
    ## 1388     76001     1113             Luis Jaime Urbano 278.25      60
    ## 1389     76002     1134 Juan Francisco Portillo Gomez 283.50      60
    ## 1390     76001     1736 Juan Francisco Portillo Gomez 434.00      60
    ## 1391     76002     1351 Juan Francisco Portillo Gomez 337.75      60
    ## 1392     76002     1041              Felipe Villatoro 260.25      60
    ## 1393     76001      397             Luis Jaime Urbano  99.25      30
    ## 1394     76001      988              Felipe Villatoro 247.00      60
    ## 1395     76001      716          Angel Valdez Alegria 179.00      60
    ## 1396     76001      459      Ismael Rodero Monteagudo 114.75      60
    ## 1397     76001     1362       Fernando Mariano Berrio 340.50      60
    ## 1398     76002      879      Ismael Rodero Monteagudo 219.75      30
    ## 1399     76002      661        Hector Aragones Frutos 165.25      30
    ## 1400     76002     1520             Luis Jaime Urbano 380.00      30
    ## 1401     76001      912          Pedro Alvarez Parejo 228.00      30
    ## 1402     76002     1534                  Hector Giron 383.50      60
    ## 1403     76001      565 Juan Francisco Portillo Gomez 141.25      30
    ## 1404     76002     1332          Angel Valdez Alegria 333.00      60
    ## 1405     76001     1725 Juan Francisco Portillo Gomez 431.25      30
    ## 1406     76001     1824              Felipe Villatoro 456.00      60
    ## 1407     76001      262              Felipe Villatoro  65.50      30
    ## 1408     76001      312       Fernando Mariano Berrio  78.00      30
    ## 1409     76001     1465      Ismael Rodero Monteagudo 366.25      90
    ## 1410     76002     1095      Ismael Rodero Monteagudo 273.75      90
    ## 1411     76001     1702      Ismael Rodero Monteagudo 425.50      60
    ## 1412     76002     1985        Hector Aragones Frutos 496.25      90
    ## 1413     76002      726                  Hector Giron 181.50      30
    ## 1414     76002     1874      Ismael Rodero Monteagudo 468.50      30
    ## 1415     76002      367      Ismael Rodero Monteagudo  91.75      30
    ## 1416     76001      347 Juan Francisco Portillo Gomez  86.75      30
    ## 1417     76002      454             Luis Jaime Urbano 113.50      30
    ## 1418     76001     1819 Juan Francisco Portillo Gomez 454.75      30
    ## 1419     76002     1993 Juan Francisco Portillo Gomez 498.25      90
    ## 1420     76002     1487      Ismael Rodero Monteagudo 371.75      90
    ## 1421     76002     1102             Luis Jaime Urbano 275.50      30
    ## 1422     76002      874          Pedro Alvarez Parejo 218.50      90
    ## 1423     76002     1290          Pedro Alvarez Parejo 322.50      60
    ## 1424     76002     1838                  Hector Giron 459.50      90
    ## 1425     76002     1762      Ismael Rodero Monteagudo 440.50      90
    ## 1426     76001      464      Ismael Rodero Monteagudo 116.00      90
    ## 1427     76002     1504             Luis Jaime Urbano 376.00      60
    ## 1428     76001      424             Luis Jaime Urbano 106.00      90
    ## 1429     76001     1599                  Hector Giron 399.75      30
    ## 1430     76001      399             Luis Jaime Urbano  99.75      30
    ## 1431     76001     1343 Juan Francisco Portillo Gomez 335.75      30
    ## 1432     76002      587              Felipe Villatoro 146.75      60
    ## 1433     76002     1839      Ismael Rodero Monteagudo 459.75      90
    ## 1434     76001     1238        Hector Aragones Frutos 309.50      90
    ## 1435     76001     1382                  Hector Giron 345.50      60
    ## 1436     76002      654 Juan Francisco Portillo Gomez 163.50      60
    ## 1437     76001      211          Pedro Alvarez Parejo  52.75      60
    ## 1438     76001      701          Pedro Alvarez Parejo 175.25      60
    ## 1439     76002     1975              Felipe Villatoro 493.75      60
    ## 1440     76002      389              Felipe Villatoro  97.25      60
    ## 1441     76002      324                  Hector Giron  81.00      90
    ## 1442     76001     1624 Juan Francisco Portillo Gomez 406.00      60
    ## 1443     76002     1936              Felipe Villatoro 484.00      60
    ## 1444     76001      996                  Hector Giron 249.00      60
    ## 1445     76002      997             Luis Jaime Urbano 249.25      30
    ## 1446     76002     1919              Felipe Villatoro 479.75      30
    ## 1447     76001     1429                  Hector Giron 357.25      30
    ## 1448     76002      885 Juan Francisco Portillo Gomez 221.25      30
    ## 1449     76002     1429          Pedro Alvarez Parejo 357.25      30
    ## 1450     76001     1682              Felipe Villatoro 420.50      30
    ## 1451     76001     1361              Felipe Villatoro 340.25      90
    ## 1452     76002     1559             Luis Jaime Urbano 389.75      60
    ## 1453     76001      704 Juan Francisco Portillo Gomez 176.00      30
    ## 1454     76002     1701                  Hector Giron 425.25      60
    ## 1455     76002      654              Felipe Villatoro 163.50      30
    ## 1456     76002     1458          Angel Valdez Alegria 364.50      30
    ## 1457     76001      909                  Hector Giron 227.25      90
    ## 1458     76001     1750          Angel Valdez Alegria 437.50      90
    ## 1459     76002      819 Juan Francisco Portillo Gomez 204.75      60
    ## 1460     76002     1496                  Hector Giron 374.00      30
    ## 1461     76002     1256                  Hector Giron 314.00      30
    ## 1462     76001     1454       Fernando Mariano Berrio 363.50      90
    ## 1463     76001      270        Hector Aragones Frutos  67.50      90
    ## 1464     76002      534          Angel Valdez Alegria 133.50      90
    ## 1465     76002     1674 Juan Francisco Portillo Gomez 418.50      30
    ## 1466     76002      217                  Hector Giron  54.25      90
    ## 1467     76001     1546 Juan Francisco Portillo Gomez 386.50      30
    ## 1468     76002     1750              Felipe Villatoro 437.50      30
    ## 1469     76001     1017             Luis Jaime Urbano 254.25      90
    ## 1470     76001      721 Juan Francisco Portillo Gomez 180.25      60
    ## 1471     76001     1916             Luis Jaime Urbano 479.00      30
    ## 1472     76001      506       Fernando Mariano Berrio 126.50      90
    ## 1473     76001      574              Felipe Villatoro 143.50      30
    ## 1474     76001     1386          Angel Valdez Alegria 346.50      90
    ## 1475     76002      214          Pedro Alvarez Parejo  53.50      90
    ## 1476     76002     1955       Fernando Mariano Berrio 488.75      60
    ## 1477     76001     1835       Fernando Mariano Berrio 458.75      60
    ## 1478     76001      692              Felipe Villatoro 173.00      60
    ## 1479     76001      650              Felipe Villatoro 162.50      90
    ## 1480     76002      650 Juan Francisco Portillo Gomez 162.50      60
    ## 1481     76001      875          Angel Valdez Alegria 218.75      30
    ## 1482     76001     1263 Juan Francisco Portillo Gomez 315.75      90
    ## 1483     76001      647                  Hector Giron 161.75      30
    ## 1484     76002      579        Hector Aragones Frutos 144.75      30
    ## 1485     76001      343 Juan Francisco Portillo Gomez  85.75      60
    ## 1486     76002      639      Ismael Rodero Monteagudo 159.75      30
    ## 1487     76002     1325                  Hector Giron 331.25      30
    ## 1488     76001      882      Ismael Rodero Monteagudo 220.50      30
    ## 1489     76001      500        Hector Aragones Frutos 125.00      60
    ## 1490     76001      871      Ismael Rodero Monteagudo 217.75      60
    ## 1491     76002     1438          Pedro Alvarez Parejo 359.50      60
    ## 1492     76002      838                  Hector Giron 209.50      30
    ## 1493     76001      519          Angel Valdez Alegria 129.75      90
    ## 1494     76002      204              Felipe Villatoro  51.00      60
    ## 1495     76001     1347       Fernando Mariano Berrio 336.75      90
    ## 1496     76001     1181      Ismael Rodero Monteagudo 295.25      90
    ## 1497     76001     1184                  Hector Giron 296.00      60
    ## 1498     76001      498 Juan Francisco Portillo Gomez 124.50      30
    ## 1499     76001      232        Hector Aragones Frutos  58.00      90
    ## 1500     76002     1175          Pedro Alvarez Parejo 293.75      60
    ## 1501     76002      361          Angel Valdez Alegria  90.25      90
    ## 1502     76001     1793      Ismael Rodero Monteagudo 448.25      30
    ## 1503     76002     1224      Ismael Rodero Monteagudo 306.00      90
    ## 1504     76002     1572      Ismael Rodero Monteagudo 393.00      30
    ## 1505     76002     1026          Pedro Alvarez Parejo 256.50      60
    ## 1506     76002     1304          Pedro Alvarez Parejo 326.00      30
    ## 1507     76001     1899          Pedro Alvarez Parejo 474.75      90
    ## 1508     76002      945          Angel Valdez Alegria 236.25      30
    ## 1509     76002      473              Felipe Villatoro 118.25      90
    ## 1510     76001     1149             Luis Jaime Urbano 287.25      60
    ## 1511     76002      421                  Hector Giron 105.25      30
    ## 1512     76002      555             Luis Jaime Urbano 138.75      60
    ## 1513     76002      374              Felipe Villatoro  93.50      90
    ## 1514     76001     1109          Pedro Alvarez Parejo 277.25      90
    ## 1515     76001     1196       Fernando Mariano Berrio 299.00      90
    ## 1516     76001      730       Fernando Mariano Berrio 182.50      30
    ## 1517     76001     1914          Pedro Alvarez Parejo 478.50      60
    ## 1518     76002      759        Hector Aragones Frutos 189.75      30
    ## 1519     76002     1432 Juan Francisco Portillo Gomez 358.00      90
    ## 1520     76002     1424                  Hector Giron 356.00      60
    ## 1521     76002     1414 Juan Francisco Portillo Gomez 353.50      60
    ## 1522     76001      504              Felipe Villatoro 126.00      90
    ## 1523     76002      361              Felipe Villatoro  90.25      60
    ## 1524     76001     1141        Hector Aragones Frutos 285.25      90
    ## 1525     76002     1985          Pedro Alvarez Parejo 496.25      90
    ## 1526     76002     1599          Pedro Alvarez Parejo 399.75      30
    ## 1527     76002      245             Luis Jaime Urbano  61.25      30
    ## 1528     76002      641        Hector Aragones Frutos 160.25      90
    ## 1529     76001      680              Felipe Villatoro 170.00      30
    ## 1530     76002      333          Pedro Alvarez Parejo  83.25      60
    ## 1531     76001     1037 Juan Francisco Portillo Gomez 259.25      30
    ## 1532     76002     1946       Fernando Mariano Berrio 486.50      90
    ## 1533     76002     1447                  Hector Giron 361.75      90
    ## 1534     76001      282                  Hector Giron  70.50      30
    ## 1535     76002      590        Hector Aragones Frutos 147.50      30
    ## 1536     76001      776       Fernando Mariano Berrio 194.00      30
    ## 1537     76002      992              Felipe Villatoro 248.00      90
    ## 1538     76001     1653      Ismael Rodero Monteagudo 413.25      60
    ## 1539     76001     1874          Angel Valdez Alegria 468.50      90
    ## 1540     76001      981          Angel Valdez Alegria 245.25      90
    ## 1541     76002     1782          Angel Valdez Alegria 445.50      60
    ## 1542     76001      514                  Hector Giron 128.50      30
    ## 1543     76001      650          Angel Valdez Alegria 162.50      30
    ## 1544     76001      874      Ismael Rodero Monteagudo 218.50      90
    ## 1545     76001      583             Luis Jaime Urbano 145.75      60
    ## 1546     76001      507             Luis Jaime Urbano 126.75      30
    ## 1547     76001     1577       Fernando Mariano Berrio 394.25      90
    ## 1548     76002     1290             Luis Jaime Urbano 322.50      90
    ## 1549     76002     1601 Juan Francisco Portillo Gomez 400.25      60
    ## 1550     76001     1689          Pedro Alvarez Parejo 422.25      60
    ## 1551     76002      899        Hector Aragones Frutos 224.75      30
    ## 1552     76002      845          Angel Valdez Alegria 211.25      90
    ## 1553     76001     1628       Fernando Mariano Berrio 407.00      30
    ## 1554     76001      413       Fernando Mariano Berrio 103.25      60
    ## 1555     76002     1832       Fernando Mariano Berrio 458.00      30
    ## 1556     76002      884       Fernando Mariano Berrio 221.00      30
    ## 1557     76002      516          Angel Valdez Alegria 129.00      90
    ## 1558     76001      671             Luis Jaime Urbano 167.75      30
    ## 1559     76002      573              Felipe Villatoro 143.25      90
    ## 1560     76001     1622          Angel Valdez Alegria 405.50      60
    ## 1561     76002      567          Pedro Alvarez Parejo 141.75      30
    ## 1562     76002      288              Felipe Villatoro  72.00      60
    ## 1563     76002      686              Felipe Villatoro 171.50      90
    ## 1564     76002      209              Felipe Villatoro  52.25      30
    ## 1565     76002     1760              Felipe Villatoro 440.00      30
    ## 1566     76002      214      Ismael Rodero Monteagudo  53.50      90
    ## 1567     76001     1072              Felipe Villatoro 268.00      90
    ## 1568     76001     1870        Hector Aragones Frutos 467.50      30
    ## 1569     76002     1028          Pedro Alvarez Parejo 257.00      30
    ## 1570     76001     1930 Juan Francisco Portillo Gomez 482.50      60
    ## 1571     76002     1540          Angel Valdez Alegria 385.00      30
    ## 1572     76001     1859              Felipe Villatoro 464.75      60
    ## 1573     76002      527          Pedro Alvarez Parejo 131.75      90
    ## 1574     76002      442          Angel Valdez Alegria 110.50      30
    ## 1575     76001     1086              Felipe Villatoro 271.50      60
    ## 1576     76002      686          Pedro Alvarez Parejo 171.50      60
    ## 1577     76001     1585      Ismael Rodero Monteagudo 396.25      60
    ## 1578     76001      287       Fernando Mariano Berrio  71.75      30
    ## 1579     76001     1559        Hector Aragones Frutos 389.75      60
    ## 1580     76002      877                  Hector Giron 219.25      30
    ## 1581     76002      380        Hector Aragones Frutos  95.00      90
    ## 1582     76001      596        Hector Aragones Frutos 149.00      90
    ## 1583     76001     1232              Felipe Villatoro 308.00      60
    ## 1584     76002     1836                  Hector Giron 459.00      30
    ## 1585     76002      594              Felipe Villatoro 148.50      30
    ## 1586     76002     1969       Fernando Mariano Berrio 492.25      90
    ## 1587     76001     1413       Fernando Mariano Berrio 353.25      60
    ## 1588     76001     1126       Fernando Mariano Berrio 281.50      90
    ## 1589     76001      248          Pedro Alvarez Parejo  62.00      90
    ## 1590     76002     1508       Fernando Mariano Berrio 377.00      30
    ## 1591     76002     1555              Felipe Villatoro 388.75      60
    ## 1592     76001     1526      Ismael Rodero Monteagudo 381.50      90
    ## 1593     76001      907       Fernando Mariano Berrio 226.75      60
    ## 1594     76001     1664      Ismael Rodero Monteagudo 416.00      30
    ## 1595     76002      567       Fernando Mariano Berrio 141.75      60
    ## 1596     76002     1617             Luis Jaime Urbano 404.25      90
    ## 1597     76002     1407              Felipe Villatoro 351.75      90
    ## 1598     76001     1006      Ismael Rodero Monteagudo 251.50      90
    ## 1599     76002     1768        Hector Aragones Frutos 442.00      60
    ## 1600     76001     1989        Hector Aragones Frutos 497.25      60
    ## 1601     76002      784              Felipe Villatoro 196.00      30
    ## 1602     76001     1499        Hector Aragones Frutos 374.75      90
    ## 1603     76001      714             Luis Jaime Urbano 178.50      30
    ## 1604     76002      704                  Hector Giron 176.00      90
    ## 1605     76001      720        Hector Aragones Frutos 180.00      90
    ## 1606     76001     1537              Felipe Villatoro 384.25      30
    ## 1607     76001      869              Felipe Villatoro 217.25      90
    ## 1608     76001     1974        Hector Aragones Frutos 493.50      90
    ## 1609     76002      686             Luis Jaime Urbano 171.50      90
    ## 1610     76001     1364          Angel Valdez Alegria 341.00      30
    ## 1611     76001     1204      Ismael Rodero Monteagudo 301.00      90
    ## 1612     76001     1466      Ismael Rodero Monteagudo 366.50      30
    ## 1613     76001     1646      Ismael Rodero Monteagudo 411.50      30
    ## 1614     76002      696        Hector Aragones Frutos 174.00      30
    ## 1615     76002      761          Angel Valdez Alegria 190.25      60
    ## 1616     76001      326          Pedro Alvarez Parejo  81.50      90
    ## 1617     76002     1672      Ismael Rodero Monteagudo 418.00      30
    ## 1618     76002     1803                  Hector Giron 450.75      60
    ## 1619     76002     1036          Angel Valdez Alegria 259.00      90
    ## 1620     76002     1729        Hector Aragones Frutos 432.25      60
    ## 1621     76002      640        Hector Aragones Frutos 160.00      30
    ## 1622     76002      768          Pedro Alvarez Parejo 192.00      30
    ## 1623     76002     1401      Ismael Rodero Monteagudo 350.25      90
    ## 1624     76001     1138             Luis Jaime Urbano 284.50      30
    ## 1625     76002      492             Luis Jaime Urbano 123.00      90
    ## 1626     76001     1524          Angel Valdez Alegria 381.00      30
    ## 1627     76001     1688             Luis Jaime Urbano 422.00      60
    ## 1628     76002     1183        Hector Aragones Frutos 295.75      30
    ## 1629     76002     1004       Fernando Mariano Berrio 251.00      90
    ## 1630     76002      319          Pedro Alvarez Parejo  79.75      90
    ## 1631     76002      360      Ismael Rodero Monteagudo  90.00      90
    ## 1632     76001      257        Hector Aragones Frutos  64.25      90
    ## 1633     76001      297 Juan Francisco Portillo Gomez  74.25      30
    ## 1634     76001      269          Pedro Alvarez Parejo  67.25      60
    ## 1635     76002      242          Angel Valdez Alegria  60.50      60
    ## 1636     76002      957       Fernando Mariano Berrio 239.25      30
    ## 1637     76001     1198        Hector Aragones Frutos 299.50      30
    ## 1638     76002     1454       Fernando Mariano Berrio 363.50      90
    ## 1639     76001     1963          Angel Valdez Alegria 490.75      30
    ## 1640     76002     1522                  Hector Giron 380.50      60
    ## 1641     76001     1261          Pedro Alvarez Parejo 315.25      90
    ## 1642     76002      660             Luis Jaime Urbano 165.00      90
    ## 1643     76002     1585       Fernando Mariano Berrio 396.25      30
    ## 1644     76002     1725      Ismael Rodero Monteagudo 431.25      90
    ## 1645     76001      843 Juan Francisco Portillo Gomez 210.75      60
    ## 1646     76001     1126          Pedro Alvarez Parejo 281.50      30
    ## 1647     76001      883        Hector Aragones Frutos 220.75      30
    ## 1648     76002      255          Angel Valdez Alegria  63.75      30
    ## 1649     76002      409          Pedro Alvarez Parejo 102.25      90
    ## 1650     76001     1793             Luis Jaime Urbano 448.25      30
    ## 1651     76001      984        Hector Aragones Frutos 246.00      30
    ## 1652     76001      245          Pedro Alvarez Parejo  61.25      30
    ## 1653     76002     1113 Juan Francisco Portillo Gomez 278.25      60
    ## 1654     76001     1278       Fernando Mariano Berrio 319.50      60
    ## 1655     76001      531                  Hector Giron 132.75      90
    ## 1656     76001      941             Luis Jaime Urbano 235.25      30
    ## 1657     76001      911          Pedro Alvarez Parejo 227.75      30
    ## 1658     76002      342                  Hector Giron  85.50      30
    ## 1659     76002     1957        Hector Aragones Frutos 489.25      90
    ## 1660     76002      514                  Hector Giron 128.50      60
    ## 1661     76002      636             Luis Jaime Urbano 159.00      60
    ## 1662     76002      563          Angel Valdez Alegria 140.75      90
    ## 1663     76001     1346          Pedro Alvarez Parejo 336.50      30
    ## 1664     76002      805          Angel Valdez Alegria 201.25      60
    ## 1665     76001      217        Hector Aragones Frutos  54.25      90
    ## 1666     76002      901        Hector Aragones Frutos 225.25      30
    ## 1667     76002      491              Felipe Villatoro 122.75      90
    ## 1668     76001     1723          Angel Valdez Alegria 430.75      90
    ## 1669     76002     1209       Fernando Mariano Berrio 302.25      60
    ## 1670     76001     1565        Hector Aragones Frutos 391.25      90
    ## 1671     76001     1866 Juan Francisco Portillo Gomez 466.50      30
    ## 1672     76002     1589              Felipe Villatoro 397.25      90
    ## 1673     76001      763             Luis Jaime Urbano 190.75      30
    ## 1674     76002     1517          Pedro Alvarez Parejo 379.25      30
    ## 1675     76002     1140          Angel Valdez Alegria 285.00      90
    ## 1676     76001     1822          Pedro Alvarez Parejo 455.50      90
    ## 1677     76001      653              Felipe Villatoro 163.25      30
    ## 1678     76002      465       Fernando Mariano Berrio 116.25      30
    ## 1679     76002     1776                  Hector Giron 444.00      90
    ## 1680     76001     1211             Luis Jaime Urbano 302.75      60
    ## 1681     76001      352        Hector Aragones Frutos  88.00      90
    ## 1682     76001      590       Fernando Mariano Berrio 147.50      90
    ## 1683     76001     1728                  Hector Giron 432.00      60
    ## 1684     76001     1240       Fernando Mariano Berrio 310.00      90
    ## 1685     76001     1832             Luis Jaime Urbano 458.00      60
    ## 1686     76002      545          Angel Valdez Alegria 136.25      60
    ## 1687     76002     1695          Pedro Alvarez Parejo 423.75      60
    ## 1688     76002      643       Fernando Mariano Berrio 160.75      30
    ## 1689     76001      427          Angel Valdez Alegria 106.75      60
    ## 1690     76002     1694          Pedro Alvarez Parejo 423.50      30
    ## 1691     76002     1083                  Hector Giron 270.75      60
    ## 1692     76002     1669       Fernando Mariano Berrio 417.25      60
    ## 1693     76001     1169        Hector Aragones Frutos 292.25      30
    ## 1694     76002     1853 Juan Francisco Portillo Gomez 463.25      30
    ## 1695     76002     1844        Hector Aragones Frutos 461.00      30
    ## 1696     76002     1740              Felipe Villatoro 435.00      60
    ## 1697     76002     1834             Luis Jaime Urbano 458.50      60
    ## 1698     76001      276      Ismael Rodero Monteagudo  69.00      30
    ## 1699     76002      241       Fernando Mariano Berrio  60.25      30
    ## 1700     76001     1492          Angel Valdez Alegria 373.00      30
    ## 1701     76001      782        Hector Aragones Frutos 195.50      30
    ## 1702     76001     1680          Angel Valdez Alegria 420.00      90
    ## 1703     76002      292                  Hector Giron  73.00      90
    ## 1704     76002      904        Hector Aragones Frutos 226.00      30
    ## 1705     76002      572                  Hector Giron 143.00      90
    ## 1706     76002      680        Hector Aragones Frutos 170.00      60
    ## 1707     76002     1339              Felipe Villatoro 334.75      30
    ## 1708     76001     1133      Ismael Rodero Monteagudo 283.25      60
    ## 1709     76002      557             Luis Jaime Urbano 139.25      30
    ## 1710     76002     1943       Fernando Mariano Berrio 485.75      30
    ## 1711     76001      432       Fernando Mariano Berrio 108.00      60
    ## 1712     76001     1990                  Hector Giron 497.50      30
    ## 1713     76002      814 Juan Francisco Portillo Gomez 203.50      30
    ## 1714     76002      998        Hector Aragones Frutos 249.50      60
    ## 1715     76001     1094             Luis Jaime Urbano 273.50      30
    ## 1716     76001     1624          Pedro Alvarez Parejo 406.00      30
    ## 1717     76001     1117 Juan Francisco Portillo Gomez 279.25      30
    ## 1718     76002     1720             Luis Jaime Urbano 430.00      90
    ## 1719     76002      892          Pedro Alvarez Parejo 223.00      90
    ## 1720     76002     1089              Felipe Villatoro 272.25      60
    ## 1721     76002     1949       Fernando Mariano Berrio 487.25      30
    ## 1722     76002     1632      Ismael Rodero Monteagudo 408.00      30
    ## 1723     76001     1273        Hector Aragones Frutos 318.25      30
    ## 1724     76001      955      Ismael Rodero Monteagudo 238.75      30
    ## 1725     76001      822          Pedro Alvarez Parejo 205.50      30
    ## 1726     76002      522          Pedro Alvarez Parejo 130.50      90
    ## 1727     76001     1372 Juan Francisco Portillo Gomez 343.00      90
    ## 1728     76002      700              Felipe Villatoro 175.00      30
    ## 1729     76001     1247          Pedro Alvarez Parejo 311.75      90
    ## 1730     76001     1940          Pedro Alvarez Parejo 485.00      60
    ## 1731     76001      700              Felipe Villatoro 175.00      30
    ## 1732     76002     1891          Pedro Alvarez Parejo 472.75      30
    ## 1733     76001     1297 Juan Francisco Portillo Gomez 324.25      90
    ## 1734     76002      275        Hector Aragones Frutos  68.75      30
    ## 1735     76001      325             Luis Jaime Urbano  81.25      30
    ## 1736     76002     1706              Felipe Villatoro 426.50      30
    ## 1737     76001      553             Luis Jaime Urbano 138.25      90
    ## 1738     76002      429             Luis Jaime Urbano 107.25      30
    ## 1739     76002     1416          Angel Valdez Alegria 354.00      90
    ## 1740     76002     1138        Hector Aragones Frutos 284.50      60
    ## 1741     76001      332          Angel Valdez Alegria  83.00      60
    ## 1742     76002      435          Pedro Alvarez Parejo 108.75      60
    ## 1743     76001     1330 Juan Francisco Portillo Gomez 332.50      60
    ## 1744     76002     1911                  Hector Giron 477.75      90
    ## 1745     76002      429                  Hector Giron 107.25      60
    ## 1746     76002     1711      Ismael Rodero Monteagudo 427.75      90
    ## 1747     76001      855              Felipe Villatoro 213.75      90
    ## 1748     76002     1443                  Hector Giron 360.75      90
    ## 1749     76002      594             Luis Jaime Urbano 148.50      90
    ## 1750     76001      671       Fernando Mariano Berrio 167.75      30
    ## 1751     76001      250       Fernando Mariano Berrio  62.50      30
    ## 1752     76001     1515             Luis Jaime Urbano 378.75      60
    ## 1753     76002      526                  Hector Giron 131.50      30
    ## 1754     76002      451          Angel Valdez Alegria 112.75      30
    ## 1755     76001     1255       Fernando Mariano Berrio 313.75      60
    ## 1756     76002      907          Angel Valdez Alegria 226.75      90
    ## 1757     76002     1959                  Hector Giron 489.75      90
    ## 1758     76002      844          Angel Valdez Alegria 211.00      90
    ## 1759     76001      815             Luis Jaime Urbano 203.75      60
    ## 1760     76001     1929       Fernando Mariano Berrio 482.25      60
    ## 1761     76001     1233          Pedro Alvarez Parejo 308.25      60
    ## 1762     76001      328          Pedro Alvarez Parejo  82.00      90
    ## 1763     76002     1224              Felipe Villatoro 306.00      30
    ## 1764     76002     1186 Juan Francisco Portillo Gomez 296.50      90
    ## 1765     76002     1945 Juan Francisco Portillo Gomez 486.25      30
    ## 1766     76001     1464       Fernando Mariano Berrio 366.00      90
    ## 1767     76002     1383        Hector Aragones Frutos 345.75      60
    ## 1768     76001      641                  Hector Giron 160.25      90
    ## 1769     76001      430       Fernando Mariano Berrio 107.50      60
    ## 1770     76001     1741                  Hector Giron 435.25      30
    ## 1771     76001     1820              Felipe Villatoro 455.00      60
    ## 1772     76002     1555              Felipe Villatoro 388.75      30
    ## 1773     76002     1754      Ismael Rodero Monteagudo 438.50      30
    ## 1774     76002     1473      Ismael Rodero Monteagudo 368.25      30
    ## 1775     76001     1632                  Hector Giron 408.00      30
    ## 1776     76002     1470                  Hector Giron 367.50      90
    ## 1777     76002     1562 Juan Francisco Portillo Gomez 390.50      60
    ## 1778     76001      293 Juan Francisco Portillo Gomez  73.25      30
    ## 1779     76001     1053          Angel Valdez Alegria 263.25      30
    ## 1780     76002      525          Angel Valdez Alegria 131.25      60
    ## 1781     76002      618                  Hector Giron 154.50      30
    ## 1782     76002      654      Ismael Rodero Monteagudo 163.50      30
    ## 1783     76002      923                  Hector Giron 230.75      60
    ## 1784     76001      511      Ismael Rodero Monteagudo 127.75      30
    ## 1785     76002      349             Luis Jaime Urbano  87.25      60
    ## 1786     76002     1278              Felipe Villatoro 319.50      60
    ## 1787     76002      356          Angel Valdez Alegria  89.00      90
    ## 1788     76001     1427          Angel Valdez Alegria 356.75      30
    ## 1789     76001     1949          Angel Valdez Alegria 487.25      90
    ## 1790     76002     1586          Pedro Alvarez Parejo 396.50      60
    ## 1791     76002     1368              Felipe Villatoro 342.00      60
    ## 1792     76002      568                  Hector Giron 142.00      60
    ## 1793     76001      864      Ismael Rodero Monteagudo 216.00      60
    ## 1794     76002     1219          Angel Valdez Alegria 304.75      60
    ## 1795     76001      425              Felipe Villatoro 106.25      90
    ## 1796     76001     1006        Hector Aragones Frutos 251.50      30
    ## 1797     76002     1882      Ismael Rodero Monteagudo 470.50      60
    ## 1798     76001      249 Juan Francisco Portillo Gomez  62.25      60
    ## 1799     76001     1323        Hector Aragones Frutos 330.75      90
    ## 1800     76001     1236 Juan Francisco Portillo Gomez 309.00      30
    ## 1801     76002     1161          Pedro Alvarez Parejo 290.25      90
    ## 1802     76001     1453                  Hector Giron 363.25      60
    ## 1803     76001      822              Felipe Villatoro 205.50      90
    ## 1804     76002     1230       Fernando Mariano Berrio 307.50      30
    ## 1805     76001      702          Pedro Alvarez Parejo 175.50      90
    ## 1806     76002     1387          Angel Valdez Alegria 346.75      90
    ## 1807     76001      412        Hector Aragones Frutos 103.00      60
    ## 1808     76002     1533      Ismael Rodero Monteagudo 383.25      30
    ## 1809     76002     1945        Hector Aragones Frutos 486.25      90
    ## 1810     76002      571 Juan Francisco Portillo Gomez 142.75      30
    ## 1811     76001     1483              Felipe Villatoro 370.75      30
    ## 1812     76001     1826                  Hector Giron 456.50      90
    ## 1813     76001     1607          Pedro Alvarez Parejo 401.75      90
    ## 1814     76002     1527       Fernando Mariano Berrio 381.75      30
    ## 1815     76002     1282              Felipe Villatoro 320.50      30
    ## 1816     76002      989          Pedro Alvarez Parejo 247.25      60
    ## 1817     76001     1439                  Hector Giron 359.75      90
    ## 1818     76002      532              Felipe Villatoro 133.00      30
    ## 1819     76002      242             Luis Jaime Urbano  60.50      60
    ## 1820     76002     1950          Pedro Alvarez Parejo 487.50      90
    ## 1821     76001     1149        Hector Aragones Frutos 287.25      60
    ## 1822     76001     1813 Juan Francisco Portillo Gomez 453.25      90
    ## 1823     76002      572              Felipe Villatoro 143.00      90
    ## 1824     76001      820          Pedro Alvarez Parejo 205.00      30
    ## 1825     76002     1105                  Hector Giron 276.25      60
    ## 1826     76001     1604        Hector Aragones Frutos 401.00      90
    ## 1827     76002      371             Luis Jaime Urbano  92.75      60
    ## 1828     76001     1365       Fernando Mariano Berrio 341.25      60
    ## 1829     76002     1796       Fernando Mariano Berrio 449.00      30
    ## 1830     76001     1443                  Hector Giron 360.75      60
    ## 1831     76002     1728          Angel Valdez Alegria 432.00      30
    ## 1832     76001      884       Fernando Mariano Berrio 221.00      60
    ## 1833     76002     1135          Angel Valdez Alegria 283.75      30
    ## 1834     76001      714          Angel Valdez Alegria 178.50      30
    ## 1835     76001     1342        Hector Aragones Frutos 335.50      30
    ## 1836     76002      549      Ismael Rodero Monteagudo 137.25      30
    ## 1837     76001     1303              Felipe Villatoro 325.75      30
    ## 1838     76002     1437          Pedro Alvarez Parejo 359.25      60
    ## 1839     76001      257      Ismael Rodero Monteagudo  64.25      60
    ## 1840     76002      429       Fernando Mariano Berrio 107.25      60
    ## 1841     76002     1231          Pedro Alvarez Parejo 307.75      60
    ## 1842     76002     1434          Pedro Alvarez Parejo 358.50      60
    ## 1843     76001     1000              Felipe Villatoro 250.00      90
    ## 1844     76002     1148      Ismael Rodero Monteagudo 287.00      90
    ## 1845     76001     1347        Hector Aragones Frutos 336.75      60
    ## 1846     76001      802        Hector Aragones Frutos 200.50      30
    ## 1847     76001     1919        Hector Aragones Frutos 479.75      30
    ## 1848     76001      717 Juan Francisco Portillo Gomez 179.25      60
    ## 1849     76002      838       Fernando Mariano Berrio 209.50      90
    ## 1850     76001      324       Fernando Mariano Berrio  81.00      90
    ## 1851     76001     1309      Ismael Rodero Monteagudo 327.25      60
    ## 1852     76001     1333                  Hector Giron 333.25      30
    ## 1853     76002     1496             Luis Jaime Urbano 374.00      90
    ## 1854     76002      327              Felipe Villatoro  81.75      30
    ## 1855     76001     1662        Hector Aragones Frutos 415.50      30
    ## 1856     76002     1479      Ismael Rodero Monteagudo 369.75      30
    ## 1857     76001      939      Ismael Rodero Monteagudo 234.75      60
    ## 1858     76002      429              Felipe Villatoro 107.25      30
    ## 1859     76002     1734                  Hector Giron 433.50      90
    ## 1860     76001      667 Juan Francisco Portillo Gomez 166.75      90
    ## 1861     76002     1054       Fernando Mariano Berrio 263.50      60
    ## 1862     76001      913              Felipe Villatoro 228.25      30
    ## 1863     76001     1583        Hector Aragones Frutos 395.75      90
    ## 1864     76002     1067                  Hector Giron 266.75      90
    ## 1865     76001     1206       Fernando Mariano Berrio 301.50      30
    ## 1866     76001     1366          Angel Valdez Alegria 341.50      30
    ## 1867     76002     1651       Fernando Mariano Berrio 412.75      90
    ## 1868     76002      481              Felipe Villatoro 120.25      90
    ## 1869     76001      975      Ismael Rodero Monteagudo 243.75      30
    ## 1870     76001      981              Felipe Villatoro 245.25      90
    ## 1871     76001      558                  Hector Giron 139.50      30
    ## 1872     76001      476          Pedro Alvarez Parejo 119.00      30
    ## 1873     76002      791       Fernando Mariano Berrio 197.75      60
    ## 1874     76002      353          Angel Valdez Alegria  88.25      60
    ## 1875     76002     1812          Angel Valdez Alegria 453.00      30
    ## 1876     76002      884              Felipe Villatoro 221.00      60
    ## 1877     76001     1055             Luis Jaime Urbano 263.75      30
    ## 1878     76002      831             Luis Jaime Urbano 207.75      60
    ## 1879     76002      623             Luis Jaime Urbano 155.75      60
    ## 1880     76001      488        Hector Aragones Frutos 122.00      30
    ## 1881     76001      980          Angel Valdez Alegria 245.00      90
    ## 1882     76002     1772                  Hector Giron 443.00      30
    ## 1883     76001     1164       Fernando Mariano Berrio 291.00      60
    ## 1884     76001      695          Angel Valdez Alegria 173.75      90
    ## 1885     76002      904          Pedro Alvarez Parejo 226.00      30
    ## 1886     76002     1022          Angel Valdez Alegria 255.50      90
    ## 1887     76001      671             Luis Jaime Urbano 167.75      60
    ## 1888     76001      523          Pedro Alvarez Parejo 130.75      60
    ## 1889     76001      988             Luis Jaime Urbano 247.00      90
    ## 1890     76001      550 Juan Francisco Portillo Gomez 137.50      30
    ## 1891     76001     1314 Juan Francisco Portillo Gomez 328.50      60
    ## 1892     76001      956 Juan Francisco Portillo Gomez 239.00      60
    ## 1893     76001     1432       Fernando Mariano Berrio 358.00      90
    ## 1894     76002      805          Pedro Alvarez Parejo 201.25      60
    ## 1895     76002     1710      Ismael Rodero Monteagudo 427.50      60
    ## 1896     76002     1496 Juan Francisco Portillo Gomez 374.00      60
    ## 1897     76002     1771              Felipe Villatoro 442.75      60
    ## 1898     76001     1416 Juan Francisco Portillo Gomez 354.00      30
    ## 1899     76001      237              Felipe Villatoro  59.25      60
    ## 1900     76002     1771          Angel Valdez Alegria 442.75      60
    ## 1901     76002      625       Fernando Mariano Berrio 156.25      30
    ## 1902     76001      254          Pedro Alvarez Parejo  63.50      30
    ## 1903     76001      789      Ismael Rodero Monteagudo 197.25      30
    ## 1904     76002     1191        Hector Aragones Frutos 297.75      90
    ## 1905     76002     1947        Hector Aragones Frutos 486.75      60
    ## 1906     76001     1121                  Hector Giron 280.25      30
    ## 1907     76002     1960      Ismael Rodero Monteagudo 490.00      60
    ## 1908     76001     1272          Pedro Alvarez Parejo 318.00      90
    ## 1909     76002      889                  Hector Giron 222.25      60
    ## 1910     76002      709          Pedro Alvarez Parejo 177.25      60
    ## 1911     76002      981              Felipe Villatoro 245.25      90
    ## 1912     76001      840      Ismael Rodero Monteagudo 210.00      90
    ## 1913     76002     1145              Felipe Villatoro 286.25      60
    ## 1914     76001      893                  Hector Giron 223.25      30
    ## 1915     76002     1674          Pedro Alvarez Parejo 418.50      30
    ## 1916     76001     1110       Fernando Mariano Berrio 277.50      90
    ## 1917     76002     1341       Fernando Mariano Berrio 335.25      60
    ## 1918     76002      999             Luis Jaime Urbano 249.75      60
    ## 1919     76001      628      Ismael Rodero Monteagudo 157.00      90
    ## 1920     76002      356             Luis Jaime Urbano  89.00      90
    ## 1921     76001     1596              Felipe Villatoro 399.00      30
    ## 1922     76002     1855      Ismael Rodero Monteagudo 463.75      60
    ## 1923     76002     1262          Pedro Alvarez Parejo 315.50      90
    ## 1924     76002      620      Ismael Rodero Monteagudo 155.00      60
    ## 1925     76001      647          Angel Valdez Alegria 161.75      30
    ## 1926     76002      417          Pedro Alvarez Parejo 104.25      60
    ## 1927     76002     1865             Luis Jaime Urbano 466.25      90
    ## 1928     76001      889       Fernando Mariano Berrio 222.25      90
    ## 1929     76001      821             Luis Jaime Urbano 205.25      90
    ## 1930     76002      918 Juan Francisco Portillo Gomez 229.50      90
    ## 1931     76002     1399                  Hector Giron 349.75      60
    ## 1932     76002      597             Luis Jaime Urbano 149.25      60
    ## 1933     76001      638      Ismael Rodero Monteagudo 159.50      30
    ## 1934     76002     1921      Ismael Rodero Monteagudo 480.25      60
    ## 1935     76001      284 Juan Francisco Portillo Gomez  71.00      90
    ## 1936     76001      387          Pedro Alvarez Parejo  96.75      60
    ## 1937     76001      374                  Hector Giron  93.50      30
    ## 1938     76002     1878          Pedro Alvarez Parejo 469.50      30
    ## 1939     76002     1969        Hector Aragones Frutos 492.25      60
    ## 1940     76001     1199             Luis Jaime Urbano 299.75      60
    ## 1941     76002     1480          Pedro Alvarez Parejo 370.00      90
    ## 1942     76002     1809          Angel Valdez Alegria 452.25      60
    ## 1943     76001     1058             Luis Jaime Urbano 264.50      60
    ## 1944     76002      708             Luis Jaime Urbano 177.00      90
    ## 1945     76002      355          Pedro Alvarez Parejo  88.75      60
    ## 1946     76002      374       Fernando Mariano Berrio  93.50      90
    ## 1947     76002     1641                  Hector Giron 410.25      90
    ## 1948     76001     1771        Hector Aragones Frutos 442.75      30
    ## 1949     76002     1166 Juan Francisco Portillo Gomez 291.50      60
    ## 1950     76002      691       Fernando Mariano Berrio 172.75      60
    ## 1951     76001     1658        Hector Aragones Frutos 414.50      30
    ## 1952     76001      670          Pedro Alvarez Parejo 167.50      30
    ## 1953     76002      832                  Hector Giron 208.00      90
    ## 1954     76001      205             Luis Jaime Urbano  51.25      60
    ## 1955     76001     1562          Pedro Alvarez Parejo 390.50      90
    ## 1956     76002      980          Pedro Alvarez Parejo 245.00      60
    ## 1957     76002     1297          Angel Valdez Alegria 324.25      90
    ## 1958     76002     1817      Ismael Rodero Monteagudo 454.25      30
    ## 1959     76002      676 Juan Francisco Portillo Gomez 169.00      90
    ## 1960     76001     1880             Luis Jaime Urbano 470.00      30
    ## 1961     76001      578       Fernando Mariano Berrio 144.50      60
    ## 1962     76001     1762          Angel Valdez Alegria 440.50      30
    ## 1963     76002     1737              Felipe Villatoro 434.25      60
    ## 1964     76002     1819              Felipe Villatoro 454.75      30
    ## 1965     76002      508              Felipe Villatoro 127.00      90
    ## 1966     76001      446      Ismael Rodero Monteagudo 111.50      90
    ## 1967     76002      597        Hector Aragones Frutos 149.25      30
    ## 1968     76002     1771      Ismael Rodero Monteagudo 442.75      90
    ## 1969     76002     1808       Fernando Mariano Berrio 452.00      30
    ## 1970     76002     1720              Felipe Villatoro 430.00      30
    ## 1971     76002     1483      Ismael Rodero Monteagudo 370.75      30
    ## 1972     76001     1155          Pedro Alvarez Parejo 288.75      90
    ## 1973     76002     1011 Juan Francisco Portillo Gomez 252.75      90
    ## 1974     76001     1228             Luis Jaime Urbano 307.00      30
    ## 1975     76001     1751 Juan Francisco Portillo Gomez 437.75      90
    ## 1976     76001     1874                  Hector Giron 468.50      30
    ## 1977     76001     1679       Fernando Mariano Berrio 419.75      60
    ## 1978     76001      945              Felipe Villatoro 236.25      90
    ## 1979     76001     1605              Felipe Villatoro 401.25      60
    ## 1980     76001     1931       Fernando Mariano Berrio 482.75      30
    ## 1981     76002      225        Hector Aragones Frutos  56.25      60
    ## 1982     76002      263       Fernando Mariano Berrio  65.75      30
    ## 1983     76002      967      Ismael Rodero Monteagudo 241.75      90
    ## 1984     76001     1639      Ismael Rodero Monteagudo 409.75      30
    ## 1985     76001     1811          Angel Valdez Alegria 452.75      60
    ## 1986     76002      676 Juan Francisco Portillo Gomez 169.00      60
    ## 1987     76001      566        Hector Aragones Frutos 141.50      90
    ## 1988     76001     1723      Ismael Rodero Monteagudo 430.75      30
    ## 1989     76001      873          Pedro Alvarez Parejo 218.25      90
    ## 1990     76001     1524          Pedro Alvarez Parejo 381.00      30
    ## 1991     76002      805          Pedro Alvarez Parejo 201.25      90
    ## 1992     76002     1382       Fernando Mariano Berrio 345.50      30
    ## 1993     76002     1430          Pedro Alvarez Parejo 357.50      60
    ## 1994     76001     1055              Felipe Villatoro 263.75      90
    ## 1995     76001     1862          Pedro Alvarez Parejo 465.50      60
    ## 1996     76002     1881       Fernando Mariano Berrio 470.25      30
    ## 1997     76002     1025          Angel Valdez Alegria 256.25      90
    ## 1998     76002      836              Felipe Villatoro 209.00      90
    ## 1999     76001      205          Pedro Alvarez Parejo  51.25      60
    ## 2000     76001     1876 Juan Francisco Portillo Gomez 469.00      30
    ## 2001     76001     1065              Felipe Villatoro 266.25      60
    ## 2002     76001     1597          Pedro Alvarez Parejo 399.25      60
    ## 2003     76001     1606             Luis Jaime Urbano 401.50      90
    ## 2004     76001     1986        Hector Aragones Frutos 496.50      60
    ## 2005     76002     1233      Ismael Rodero Monteagudo 308.25      90
    ## 2006     76002     1757       Fernando Mariano Berrio 439.25      90
    ## 2007     76001      477 Juan Francisco Portillo Gomez 119.25      60
    ## 2008     76001      531          Pedro Alvarez Parejo 132.75      30
    ## 2009     76001      826              Felipe Villatoro 206.50      30
    ## 2010     76001     1075        Hector Aragones Frutos 268.75      30
    ## 2011     76001     1556          Angel Valdez Alegria 389.00      90
    ## 2012     76001     1850 Juan Francisco Portillo Gomez 462.50      60
    ## 2013     76002      359          Pedro Alvarez Parejo  89.75      60
    ## 2014     76002     1173          Angel Valdez Alegria 293.25      30
    ## 2015     76002     1883             Luis Jaime Urbano 470.75      90
    ## 2016     76002      289      Ismael Rodero Monteagudo  72.25      60
    ## 2017     76002     1087 Juan Francisco Portillo Gomez 271.75      90
    ## 2018     76001      946       Fernando Mariano Berrio 236.50      30
    ## 2019     76002     1950          Pedro Alvarez Parejo 487.50      60
    ## 2020     76002      938       Fernando Mariano Berrio 234.50      60
    ## 2021     76001     1092      Ismael Rodero Monteagudo 273.00      60
    ## 2022     76002     1256             Luis Jaime Urbano 314.00      90
    ## 2023     76002      959        Hector Aragones Frutos 239.75      60
    ## 2024     76002     1699          Angel Valdez Alegria 424.75      60
    ## 2025     76001      612          Pedro Alvarez Parejo 153.00      30
    ## 2026     76002     1991              Felipe Villatoro 497.75      30
    ## 2027     76001     1105          Angel Valdez Alegria 276.25      30
    ## 2028     76001     1973      Ismael Rodero Monteagudo 493.25      60
    ## 2029     76002      768             Luis Jaime Urbano 192.00      30
    ## 2030     76002     1364       Fernando Mariano Berrio 341.00      90
    ## 2031     76001      838             Luis Jaime Urbano 209.50      60
    ## 2032     76001      641        Hector Aragones Frutos 160.25      90
    ## 2033     76002     1842          Angel Valdez Alegria 460.50      60
    ## 2034     76001      505                  Hector Giron 126.25      60
    ## 2035     76002     1817          Pedro Alvarez Parejo 454.25      90
    ## 2036     76001      890          Angel Valdez Alegria 222.50      30
    ## 2037     76001      466          Pedro Alvarez Parejo 116.50      30
    ## 2038     76001      410          Pedro Alvarez Parejo 102.50      60
    ## 2039     76001      599        Hector Aragones Frutos 149.75      30
    ## 2040     76001     1771      Ismael Rodero Monteagudo 442.75      60
    ## 2041     76002      632 Juan Francisco Portillo Gomez 158.00      60
    ## 2042     76001     1935      Ismael Rodero Monteagudo 483.75      60
    ## 2043     76002     1761       Fernando Mariano Berrio 440.25      60
    ## 2044     76002      952              Felipe Villatoro 238.00      90
    ## 2045     76002      640      Ismael Rodero Monteagudo 160.00      90
    ## 2046     76002     1103       Fernando Mariano Berrio 275.75      90
    ## 2047     76002     1577       Fernando Mariano Berrio 394.25      90
    ## 2048     76001     1778             Luis Jaime Urbano 444.50      30
    ## 2049     76002     1595       Fernando Mariano Berrio 398.75      60
    ## 2050     76001     1857              Felipe Villatoro 464.25      60
    ## 2051     76002      554                  Hector Giron 138.50      90
    ## 2052     76001     1501                  Hector Giron 375.25      90
    ## 2053     76001      966 Juan Francisco Portillo Gomez 241.50      90
    ## 2054     76001     1813             Luis Jaime Urbano 453.25      90
    ## 2055     76001     1419              Felipe Villatoro 354.75      30
    ## 2056     76002     1512              Felipe Villatoro 378.00      60
    ## 2057     76002      295        Hector Aragones Frutos  73.75      30
    ## 2058     76002     1775                  Hector Giron 443.75      90
    ## 2059     76001      334          Pedro Alvarez Parejo  83.50      30
    ## 2060     76002     1184          Angel Valdez Alegria 296.00      60
    ## 2061     76002     1873        Hector Aragones Frutos 468.25      30
    ## 2062     76002     1096          Pedro Alvarez Parejo 274.00      60
    ## 2063     76001     1387                  Hector Giron 346.75      90
    ## 2064     76002     1043             Luis Jaime Urbano 260.75      90
    ## 2065     76002      691        Hector Aragones Frutos 172.75      60
    ## 2066     76002     1731       Fernando Mariano Berrio 432.75      60
    ## 2067     76002     1804        Hector Aragones Frutos 451.00      60
    ## 2068     76001      200              Felipe Villatoro  50.00      60
    ## 2069     76001      377              Felipe Villatoro  94.25      90
    ## 2070     76001     1673          Pedro Alvarez Parejo 418.25      90
    ## 2071     76002     1640          Angel Valdez Alegria 410.00      60
    ## 2072     76001      623       Fernando Mariano Berrio 155.75      30
    ## 2073     76001      870       Fernando Mariano Berrio 217.50      30
    ## 2074     76001      233          Pedro Alvarez Parejo  58.25      30
    ## 2075     76002      894       Fernando Mariano Berrio 223.50      30
    ## 2076     76001      207          Angel Valdez Alegria  51.75      60
    ## 2077     76002     1472 Juan Francisco Portillo Gomez 368.00      30
    ## 2078     76001      643        Hector Aragones Frutos 160.75      30
    ## 2079     76002      961       Fernando Mariano Berrio 240.25      60
    ## 2080     76002     1557 Juan Francisco Portillo Gomez 389.25      60
    ## 2081     76001     1273          Angel Valdez Alegria 318.25      90
    ## 2082     76001      398              Felipe Villatoro  99.50      30
    ## 2083     76002      986      Ismael Rodero Monteagudo 246.50      30
    ## 2084     76001     1569                  Hector Giron 392.25      90
    ## 2085     76001     1795       Fernando Mariano Berrio 448.75      30
    ## 2086     76001     1838 Juan Francisco Portillo Gomez 459.50      30
    ## 2087     76001     1151        Hector Aragones Frutos 287.75      30
    ## 2088     76001      304             Luis Jaime Urbano  76.00      90
    ## 2089     76001      247                  Hector Giron  61.75      90
    ## 2090     76002     1579             Luis Jaime Urbano 394.75      60
    ## 2091     76001     1727          Pedro Alvarez Parejo 431.75      90
    ## 2092     76002      801 Juan Francisco Portillo Gomez 200.25      60
    ## 2093     76001     1458       Fernando Mariano Berrio 364.50      30
    ## 2094     76002      687                  Hector Giron 171.75      60
    ## 2095     76001      503        Hector Aragones Frutos 125.75      30
    ## 2096     76002      683             Luis Jaime Urbano 170.75      30
    ## 2097     76001     1427                  Hector Giron 356.75      90
    ## 2098     76001     1013          Pedro Alvarez Parejo 253.25      30
    ## 2099     76001     1720          Angel Valdez Alegria 430.00      30
    ## 2100     76001      770                  Hector Giron 192.50      30
    ## 2101     76002     1934 Juan Francisco Portillo Gomez 483.50      90
    ## 2102     76001      743          Pedro Alvarez Parejo 185.75      60
    ## 2103     76002     1850              Felipe Villatoro 462.50      30
    ## 2104     76002      875              Felipe Villatoro 218.75      30
    ## 2105     76001     1919        Hector Aragones Frutos 479.75      90
    ## 2106     76002     1073       Fernando Mariano Berrio 268.25      30
    ## 2107     76002      902        Hector Aragones Frutos 225.50      60
    ## 2108     76001      203                  Hector Giron  50.75      60
    ## 2109     76002      659       Fernando Mariano Berrio 164.75      60
    ## 2110     76002     1204              Felipe Villatoro 301.00      30
    ## 2111     76002     1967             Luis Jaime Urbano 491.75      30
    ## 2112     76001     1837      Ismael Rodero Monteagudo 459.25      90
    ## 2113     76001      681          Pedro Alvarez Parejo 170.25      90
    ## 2114     76002      451 Juan Francisco Portillo Gomez 112.75      30
    ## 2115     76001     1670             Luis Jaime Urbano 417.50      90
    ## 2116     76001     1986        Hector Aragones Frutos 496.50      60
    ## 2117     76001     1091        Hector Aragones Frutos 272.75      90
    ## 2118     76002     1302          Angel Valdez Alegria 325.50      60
    ## 2119     76002     1779      Ismael Rodero Monteagudo 444.75      30
    ## 2120     76001      970 Juan Francisco Portillo Gomez 242.50      60
    ## 2121     76002     1766          Pedro Alvarez Parejo 441.50      60
    ## 2122     76002     1062 Juan Francisco Portillo Gomez 265.50      60
    ## 2123     76002     1804          Angel Valdez Alegria 451.00      30
    ## 2124     76002     1440          Pedro Alvarez Parejo 360.00      30
    ## 2125     76002     1353                  Hector Giron 338.25      90
    ## 2126     76002     1144      Ismael Rodero Monteagudo 286.00      30
    ## 2127     76001     1366          Pedro Alvarez Parejo 341.50      30
    ## 2128     76001      228 Juan Francisco Portillo Gomez  57.00      30
    ## 2129     76002      247          Pedro Alvarez Parejo  61.75      90
    ## 2130     76001     1152                  Hector Giron 288.00      30
    ## 2131     76002      758       Fernando Mariano Berrio 189.50      90
    ## 2132     76002      813 Juan Francisco Portillo Gomez 203.25      60
    ## 2133     76001     1598        Hector Aragones Frutos 399.50      30
    ## 2134     76002     1379 Juan Francisco Portillo Gomez 344.75      90
    ## 2135     76002     1258             Luis Jaime Urbano 314.50      60
    ## 2136     76002     1564        Hector Aragones Frutos 391.00      30
    ## 2137     76002     1626          Angel Valdez Alegria 406.50      60
    ## 2138     76002     1866              Felipe Villatoro 466.50      90
    ## 2139     76001      619          Angel Valdez Alegria 154.75      90
    ## 2140     76002     1130       Fernando Mariano Berrio 282.50      90
    ## 2141     76002     1623          Pedro Alvarez Parejo 405.75      60
    ## 2142     76001     1981             Luis Jaime Urbano 495.25      30
    ## 2143     76001      601       Fernando Mariano Berrio 150.25      30
    ## 2144     76002      428        Hector Aragones Frutos 107.00      60
    ## 2145     76001      259          Angel Valdez Alegria  64.75      90
    ## 2146     76002     1767             Luis Jaime Urbano 441.75      30
    ## 2147     76002     1213        Hector Aragones Frutos 303.25      60
    ## 2148     76001      866 Juan Francisco Portillo Gomez 216.50      60
    ## 2149     76002     1118          Angel Valdez Alegria 279.50      60
    ## 2150     76001     1397          Angel Valdez Alegria 349.25      60
    ## 2151     76001     1125       Fernando Mariano Berrio 281.25      30
    ## 2152     76001     1904       Fernando Mariano Berrio 476.00      90
    ## 2153     76001      496                  Hector Giron 124.00      60
    ## 2154     76002     1064      Ismael Rodero Monteagudo 266.00      90
    ## 2155     76001     1100 Juan Francisco Portillo Gomez 275.00      90
    ## 2156     76002     1010 Juan Francisco Portillo Gomez 252.50      60
    ## 2157     76002     1174      Ismael Rodero Monteagudo 293.50      30
    ## 2158     76002      941          Pedro Alvarez Parejo 235.25      60
    ## 2159     76001      988          Pedro Alvarez Parejo 247.00      30
    ## 2160     76002     1636       Fernando Mariano Berrio 409.00      30
    ## 2161     76001     1401                  Hector Giron 350.25      30
    ## 2162     76002     1854          Pedro Alvarez Parejo 463.50      90
    ## 2163     76002      836 Juan Francisco Portillo Gomez 209.00      90
    ## 2164     76002     1302          Pedro Alvarez Parejo 325.50      90
    ## 2165     76002      235 Juan Francisco Portillo Gomez  58.75      30
    ## 2166     76001      977                  Hector Giron 244.25      30
    ## 2167     76001     1970              Felipe Villatoro 492.50      60
    ## 2168     76001      413          Pedro Alvarez Parejo 103.25      60
    ## 2169     76002     1573       Fernando Mariano Berrio 393.25      30
    ## 2170     76001     1564 Juan Francisco Portillo Gomez 391.00      90
    ## 2171     76002      908          Pedro Alvarez Parejo 227.00      60
    ## 2172     76002     1727        Hector Aragones Frutos 431.75      90
    ## 2173     76002     1774 Juan Francisco Portillo Gomez 443.50      30
    ## 2174     76001     1476                  Hector Giron 369.00      30
    ## 2175     76001      701       Fernando Mariano Berrio 175.25      60
    ## 2176     76002      808          Pedro Alvarez Parejo 202.00      90
    ## 2177     76001      995             Luis Jaime Urbano 248.75      60
    ## 2178     76002     1743 Juan Francisco Portillo Gomez 435.75      90
    ## 2179     76001      883       Fernando Mariano Berrio 220.75      90
    ## 2180     76001     1062          Angel Valdez Alegria 265.50      90
    ##              UNIDAD mes anio
    ## 1     Camion Grande  01 2018
    ## 2     Camion Grande  01 2018
    ## 3     Camion Grande  01 2018
    ## 4             Panel  01 2018
    ## 5     Camion Grande  01 2018
    ## 6     Camion Grande  01 2018
    ## 7     Camion Grande  01 2018
    ## 8     Camion Grande  01 2018
    ## 9     Camion Grande  01 2018
    ## 10    Camion Grande  01 2018
    ## 11    Camion Grande  01 2018
    ## 12            Panel  01 2018
    ## 13    Camion Grande  01 2018
    ## 14            Panel  01 2018
    ## 15    Camion Grande  01 2018
    ## 16    Camion Grande  01 2018
    ## 17    Camion Grande  01 2018
    ## 18            Panel  01 2018
    ## 19   Camion Pequeño  01 2018
    ## 20   Camion Pequeño  01 2018
    ## 21   Camion Pequeño  01 2018
    ## 22    Camion Grande  01 2018
    ## 23            Panel  01 2018
    ## 24    Camion Grande  01 2018
    ## 25    Camion Grande  01 2018
    ## 26   Camion Pequeño  01 2018
    ## 27   Camion Pequeño  01 2018
    ## 28    Camion Grande  01 2018
    ## 29    Camion Grande  01 2018
    ## 30    Camion Grande  01 2018
    ## 31    Camion Grande  01 2018
    ## 32    Camion Grande  01 2018
    ## 33   Camion Pequeño  01 2018
    ## 34            Panel  01 2018
    ## 35    Camion Grande  01 2018
    ## 36    Camion Grande  01 2018
    ## 37    Camion Grande  01 2018
    ## 38    Camion Grande  01 2018
    ## 39    Camion Grande  01 2018
    ## 40   Camion Pequeño  01 2018
    ## 41   Camion Pequeño  01 2018
    ## 42   Camion Pequeño  01 2018
    ## 43    Camion Grande  01 2018
    ## 44    Camion Grande  01 2018
    ## 45    Camion Grande  01 2018
    ## 46   Camion Pequeño  01 2018
    ## 47            Panel  01 2018
    ## 48    Camion Grande  01 2018
    ## 49            Panel  01 2018
    ## 50            Panel  01 2018
    ## 51            Panel  01 2018
    ## 52   Camion Pequeño  01 2018
    ## 53    Camion Grande  01 2018
    ## 54            Panel  01 2018
    ## 55    Camion Grande  01 2018
    ## 56    Camion Grande  01 2018
    ## 57    Camion Grande  01 2018
    ## 58    Camion Grande  01 2018
    ## 59    Camion Grande  01 2018
    ## 60    Camion Grande  01 2018
    ## 61    Camion Grande  01 2018
    ## 62    Camion Grande  01 2018
    ## 63    Camion Grande  01 2018
    ## 64    Camion Grande  01 2018
    ## 65    Camion Grande  01 2018
    ## 66    Camion Grande  01 2018
    ## 67    Camion Grande  01 2018
    ## 68   Camion Pequeño  01 2018
    ## 69    Camion Grande  01 2018
    ## 70    Camion Grande  01 2018
    ## 71    Camion Grande  01 2018
    ## 72   Camion Pequeño  01 2018
    ## 73    Camion Grande  01 2018
    ## 74    Camion Grande  01 2018
    ## 75   Camion Pequeño  01 2018
    ## 76    Camion Grande  01 2018
    ## 77    Camion Grande  01 2018
    ## 78    Camion Grande  01 2018
    ## 79   Camion Pequeño  01 2018
    ## 80    Camion Grande  01 2018
    ## 81   Camion Pequeño  01 2018
    ## 82   Camion Pequeño  01 2018
    ## 83    Camion Grande  01 2018
    ## 84    Camion Grande  01 2018
    ## 85            Panel  01 2018
    ## 86    Camion Grande  01 2018
    ## 87   Camion Pequeño  01 2018
    ## 88   Camion Pequeño  01 2018
    ## 89   Camion Pequeño  01 2018
    ## 90    Camion Grande  01 2018
    ## 91    Camion Grande  01 2018
    ## 92    Camion Grande  01 2018
    ## 93    Camion Grande  01 2018
    ## 94    Camion Grande  01 2018
    ## 95    Camion Grande  01 2018
    ## 96   Camion Pequeño  01 2018
    ## 97   Camion Pequeño  01 2018
    ## 98    Camion Grande  01 2018
    ## 99    Camion Grande  01 2018
    ## 100   Camion Grande  01 2018
    ## 101   Camion Grande  01 2018
    ## 102   Camion Grande  01 2018
    ## 103   Camion Grande  01 2018
    ## 104  Camion Pequeño  01 2018
    ## 105  Camion Pequeño  01 2018
    ## 106           Panel  01 2018
    ## 107   Camion Grande  01 2018
    ## 108   Camion Grande  01 2018
    ## 109  Camion Pequeño  01 2018
    ## 110  Camion Pequeño  01 2018
    ## 111           Panel  01 2018
    ## 112   Camion Grande  01 2018
    ## 113   Camion Grande  01 2018
    ## 114   Camion Grande  01 2018
    ## 115  Camion Pequeño  01 2018
    ## 116  Camion Pequeño  01 2018
    ## 117   Camion Grande  01 2018
    ## 118   Camion Grande  01 2018
    ## 119   Camion Grande  01 2018
    ## 120   Camion Grande  01 2018
    ## 121   Camion Grande  01 2018
    ## 122   Camion Grande  01 2018
    ## 123   Camion Grande  01 2018
    ## 124   Camion Grande  01 2018
    ## 125   Camion Grande  01 2018
    ## 126   Camion Grande  01 2018
    ## 127  Camion Pequeño  01 2018
    ## 128   Camion Grande  01 2018
    ## 129           Panel  01 2018
    ## 130   Camion Grande  01 2018
    ## 131   Camion Grande  01 2018
    ## 132           Panel  01 2018
    ## 133           Panel  01 2018
    ## 134           Panel  01 2018
    ## 135   Camion Grande  01 2018
    ## 136   Camion Grande  01 2018
    ## 137   Camion Grande  01 2018
    ## 138   Camion Grande  01 2018
    ## 139   Camion Grande  01 2018
    ## 140   Camion Grande  01 2018
    ## 141   Camion Grande  01 2018
    ## 142  Camion Pequeño  01 2018
    ## 143   Camion Grande  01 2018
    ## 144  Camion Pequeño  01 2018
    ## 145   Camion Grande  01 2018
    ## 146           Panel  01 2018
    ## 147  Camion Pequeño  01 2018
    ## 148           Panel  01 2018
    ## 149  Camion Pequeño  01 2018
    ## 150   Camion Grande  01 2018
    ## 151   Camion Grande  01 2018
    ## 152  Camion Pequeño  01 2018
    ## 153   Camion Grande  01 2018
    ## 154   Camion Grande  01 2018
    ## 155           Panel  01 2018
    ## 156           Panel  01 2018
    ## 157   Camion Grande  01 2018
    ## 158   Camion Grande  01 2018
    ## 159  Camion Pequeño  01 2018
    ## 160           Panel  01 2018
    ## 161  Camion Pequeño  01 2018
    ## 162           Panel  01 2018
    ## 163   Camion Grande  01 2018
    ## 164   Camion Grande  01 2018
    ## 165           Panel  01 2018
    ## 166  Camion Pequeño  01 2018
    ## 167  Camion Pequeño  01 2018
    ## 168  Camion Pequeño  01 2018
    ## 169   Camion Grande  01 2018
    ## 170  Camion Pequeño  01 2018
    ## 171   Camion Grande  01 2018
    ## 172   Camion Grande  01 2018
    ## 173   Camion Grande  01 2018
    ## 174   Camion Grande  01 2018
    ## 175   Camion Grande  01 2018
    ## 176  Camion Pequeño  01 2018
    ## 177   Camion Grande  01 2018
    ## 178   Camion Grande  01 2018
    ## 179   Camion Grande  01 2018
    ## 180  Camion Pequeño  01 2018
    ## 181   Camion Grande  01 2018
    ## 182   Camion Grande  01 2018
    ## 183   Camion Grande  01 2018
    ## 184  Camion Pequeño  01 2018
    ## 185   Camion Grande  01 2018
    ## 186   Camion Grande  01 2018
    ## 187   Camion Grande  01 2018
    ## 188           Panel  01 2018
    ## 189   Camion Grande  01 2018
    ## 190   Camion Grande  01 2018
    ## 191   Camion Grande  01 2018
    ## 192           Panel  01 2018
    ## 193  Camion Pequeño  02 2018
    ## 194  Camion Pequeño  02 2018
    ## 195           Panel  02 2018
    ## 196           Panel  02 2018
    ## 197   Camion Grande  02 2018
    ## 198  Camion Pequeño  02 2018
    ## 199   Camion Grande  02 2018
    ## 200   Camion Grande  02 2018
    ## 201   Camion Grande  02 2018
    ## 202  Camion Pequeño  02 2018
    ## 203   Camion Grande  02 2018
    ## 204   Camion Grande  02 2018
    ## 205   Camion Grande  02 2018
    ## 206   Camion Grande  02 2018
    ## 207   Camion Grande  02 2018
    ## 208   Camion Grande  02 2018
    ## 209           Panel  02 2018
    ## 210  Camion Pequeño  02 2018
    ## 211   Camion Grande  02 2018
    ## 212   Camion Grande  02 2018
    ## 213   Camion Grande  02 2018
    ## 214   Camion Grande  02 2018
    ## 215  Camion Pequeño  02 2018
    ## 216   Camion Grande  02 2018
    ## 217  Camion Pequeño  02 2018
    ## 218   Camion Grande  02 2018
    ## 219   Camion Grande  02 2018
    ## 220   Camion Grande  02 2018
    ## 221   Camion Grande  02 2018
    ## 222  Camion Pequeño  02 2018
    ## 223   Camion Grande  02 2018
    ## 224   Camion Grande  02 2018
    ## 225   Camion Grande  02 2018
    ## 226   Camion Grande  02 2018
    ## 227  Camion Pequeño  02 2018
    ## 228   Camion Grande  02 2018
    ## 229   Camion Grande  02 2018
    ## 230  Camion Pequeño  02 2018
    ## 231   Camion Grande  02 2018
    ## 232           Panel  02 2018
    ## 233   Camion Grande  02 2018
    ## 234   Camion Grande  02 2018
    ## 235           Panel  02 2018
    ## 236   Camion Grande  02 2018
    ## 237  Camion Pequeño  02 2018
    ## 238  Camion Pequeño  02 2018
    ## 239  Camion Pequeño  02 2018
    ## 240   Camion Grande  02 2018
    ## 241   Camion Grande  02 2018
    ## 242   Camion Grande  02 2018
    ## 243   Camion Grande  02 2018
    ## 244   Camion Grande  02 2018
    ## 245   Camion Grande  02 2018
    ## 246  Camion Pequeño  02 2018
    ## 247   Camion Grande  02 2018
    ## 248   Camion Grande  02 2018
    ## 249   Camion Grande  02 2018
    ## 250   Camion Grande  02 2018
    ## 251   Camion Grande  02 2018
    ## 252  Camion Pequeño  02 2018
    ## 253   Camion Grande  02 2018
    ## 254           Panel  02 2018
    ## 255   Camion Grande  02 2018
    ## 256           Panel  02 2018
    ## 257  Camion Pequeño  02 2018
    ## 258   Camion Grande  02 2018
    ## 259           Panel  02 2018
    ## 260           Panel  02 2018
    ## 261   Camion Grande  02 2018
    ## 262   Camion Grande  02 2018
    ## 263           Panel  02 2018
    ## 264   Camion Grande  02 2018
    ## 265  Camion Pequeño  02 2018
    ## 266   Camion Grande  02 2018
    ## 267  Camion Pequeño  02 2018
    ## 268  Camion Pequeño  02 2018
    ## 269  Camion Pequeño  02 2018
    ## 270   Camion Grande  02 2018
    ## 271  Camion Pequeño  02 2018
    ## 272  Camion Pequeño  02 2018
    ## 273   Camion Grande  02 2018
    ## 274  Camion Pequeño  02 2018
    ## 275           Panel  02 2018
    ## 276   Camion Grande  02 2018
    ## 277  Camion Pequeño  02 2018
    ## 278  Camion Pequeño  02 2018
    ## 279   Camion Grande  02 2018
    ## 280  Camion Pequeño  02 2018
    ## 281   Camion Grande  02 2018
    ## 282   Camion Grande  02 2018
    ## 283   Camion Grande  02 2018
    ## 284   Camion Grande  02 2018
    ## 285   Camion Grande  02 2018
    ## 286   Camion Grande  02 2018
    ## 287   Camion Grande  02 2018
    ## 288   Camion Grande  02 2018
    ## 289   Camion Grande  02 2018
    ## 290   Camion Grande  02 2018
    ## 291   Camion Grande  02 2018
    ## 292           Panel  02 2018
    ## 293   Camion Grande  02 2018
    ## 294   Camion Grande  02 2018
    ## 295   Camion Grande  02 2018
    ## 296  Camion Pequeño  02 2018
    ## 297           Panel  02 2018
    ## 298  Camion Pequeño  02 2018
    ## 299   Camion Grande  02 2018
    ## 300  Camion Pequeño  02 2018
    ## 301  Camion Pequeño  02 2018
    ## 302   Camion Grande  02 2018
    ## 303   Camion Grande  02 2018
    ## 304   Camion Grande  02 2018
    ## 305   Camion Grande  02 2018
    ## 306  Camion Pequeño  02 2018
    ## 307   Camion Grande  02 2018
    ## 308           Panel  02 2018
    ## 309           Panel  02 2018
    ## 310           Panel  02 2018
    ## 311   Camion Grande  02 2018
    ## 312   Camion Grande  02 2018
    ## 313   Camion Grande  02 2018
    ## 314   Camion Grande  02 2018
    ## 315           Panel  02 2018
    ## 316   Camion Grande  02 2018
    ## 317   Camion Grande  02 2018
    ## 318   Camion Grande  02 2018
    ## 319  Camion Pequeño  02 2018
    ## 320   Camion Grande  02 2018
    ## 321  Camion Pequeño  02 2018
    ## 322  Camion Pequeño  02 2018
    ## 323           Panel  02 2018
    ## 324   Camion Grande  02 2018
    ## 325           Panel  02 2018
    ## 326   Camion Grande  02 2018
    ## 327  Camion Pequeño  02 2018
    ## 328   Camion Grande  02 2018
    ## 329   Camion Grande  02 2018
    ## 330  Camion Pequeño  02 2018
    ## 331  Camion Pequeño  02 2018
    ## 332  Camion Pequeño  02 2018
    ## 333   Camion Grande  02 2018
    ## 334  Camion Pequeño  02 2018
    ## 335   Camion Grande  02 2018
    ## 336   Camion Grande  02 2018
    ## 337  Camion Pequeño  02 2018
    ## 338  Camion Pequeño  02 2018
    ## 339           Panel  02 2018
    ## 340   Camion Grande  02 2018
    ## 341   Camion Grande  02 2018
    ## 342   Camion Grande  02 2018
    ## 343   Camion Grande  02 2018
    ## 344  Camion Pequeño  02 2018
    ## 345   Camion Grande  02 2018
    ## 346  Camion Pequeño  02 2018
    ## 347           Panel  02 2018
    ## 348   Camion Grande  02 2018
    ## 349  Camion Pequeño  02 2018
    ## 350           Panel  02 2018
    ## 351   Camion Grande  02 2018
    ## 352   Camion Grande  02 2018
    ## 353   Camion Grande  02 2018
    ## 354   Camion Grande  02 2018
    ## 355   Camion Grande  02 2018
    ## 356   Camion Grande  02 2018
    ## 357           Panel  02 2018
    ## 358           Panel  02 2018
    ## 359   Camion Grande  02 2018
    ## 360  Camion Pequeño  02 2018
    ## 361   Camion Grande  02 2018
    ## 362   Camion Grande  02 2018
    ## 363   Camion Grande  02 2018
    ## 364   Camion Grande  02 2018
    ## 365  Camion Pequeño  02 2018
    ## 366   Camion Grande  02 2018
    ## 367  Camion Pequeño  02 2018
    ## 368   Camion Grande  02 2018
    ## 369           Panel  02 2018
    ## 370   Camion Grande  02 2018
    ## 371           Panel  02 2018
    ## 372   Camion Grande  02 2018
    ## 373  Camion Pequeño  02 2018
    ## 374           Panel  02 2018
    ## 375           Panel  02 2018
    ## 376   Camion Grande  02 2018
    ## 377           Panel  02 2018
    ## 378  Camion Pequeño  02 2018
    ## 379           Panel  02 2018
    ## 380   Camion Grande  02 2018
    ## 381  Camion Pequeño  02 2018
    ## 382  Camion Pequeño  02 2018
    ## 383   Camion Grande  02 2018
    ## 384   Camion Grande  02 2018
    ## 385  Camion Pequeño  02 2018
    ## 386           Panel  02 2018
    ## 387           Panel  02 2018
    ## 388   Camion Grande  02 2018
    ## 389   Camion Grande  02 2018
    ## 390  Camion Pequeño  02 2018
    ## 391   Camion Grande  02 2018
    ## 392  Camion Pequeño  02 2018
    ## 393           Panel  02 2018
    ## 394           Panel  02 2018
    ## 395           Panel  02 2018
    ## 396   Camion Grande  03 2018
    ## 397   Camion Grande  03 2018
    ## 398           Panel  03 2018
    ## 399  Camion Pequeño  03 2018
    ## 400           Panel  03 2018
    ## 401   Camion Grande  03 2018
    ## 402   Camion Grande  03 2018
    ## 403  Camion Pequeño  03 2018
    ## 404           Panel  03 2018
    ## 405  Camion Pequeño  03 2018
    ## 406   Camion Grande  03 2018
    ## 407   Camion Grande  03 2018
    ## 408   Camion Grande  03 2018
    ## 409   Camion Grande  03 2018
    ## 410   Camion Grande  03 2018
    ## 411           Panel  03 2018
    ## 412   Camion Grande  03 2018
    ## 413  Camion Pequeño  03 2018
    ## 414   Camion Grande  03 2018
    ## 415   Camion Grande  03 2018
    ## 416  Camion Pequeño  03 2018
    ## 417           Panel  03 2018
    ## 418  Camion Pequeño  03 2018
    ## 419   Camion Grande  03 2018
    ## 420   Camion Grande  03 2018
    ## 421   Camion Grande  03 2018
    ## 422           Panel  03 2018
    ## 423   Camion Grande  03 2018
    ## 424           Panel  03 2018
    ## 425           Panel  03 2018
    ## 426   Camion Grande  03 2018
    ## 427           Panel  03 2018
    ## 428           Panel  03 2018
    ## 429   Camion Grande  03 2018
    ## 430  Camion Pequeño  03 2018
    ## 431           Panel  03 2018
    ## 432  Camion Pequeño  03 2018
    ## 433           Panel  03 2018
    ## 434   Camion Grande  03 2018
    ## 435           Panel  03 2018
    ## 436   Camion Grande  03 2018
    ## 437           Panel  03 2018
    ## 438   Camion Grande  03 2018
    ## 439   Camion Grande  03 2018
    ## 440  Camion Pequeño  03 2018
    ## 441           Panel  03 2018
    ## 442           Panel  03 2018
    ## 443   Camion Grande  03 2018
    ## 444   Camion Grande  03 2018
    ## 445           Panel  03 2018
    ## 446  Camion Pequeño  03 2018
    ## 447   Camion Grande  03 2018
    ## 448  Camion Pequeño  03 2018
    ## 449   Camion Grande  03 2018
    ## 450  Camion Pequeño  03 2018
    ## 451   Camion Grande  03 2018
    ## 452   Camion Grande  03 2018
    ## 453  Camion Pequeño  03 2018
    ## 454  Camion Pequeño  03 2018
    ## 455  Camion Pequeño  03 2018
    ## 456   Camion Grande  03 2018
    ## 457   Camion Grande  03 2018
    ## 458  Camion Pequeño  03 2018
    ## 459           Panel  03 2018
    ## 460           Panel  03 2018
    ## 461           Panel  03 2018
    ## 462  Camion Pequeño  03 2018
    ## 463  Camion Pequeño  03 2018
    ## 464  Camion Pequeño  03 2018
    ## 465   Camion Grande  03 2018
    ## 466   Camion Grande  03 2018
    ## 467   Camion Grande  03 2018
    ## 468   Camion Grande  03 2018
    ## 469   Camion Grande  03 2018
    ## 470   Camion Grande  03 2018
    ## 471   Camion Grande  03 2018
    ## 472   Camion Grande  03 2018
    ## 473  Camion Pequeño  03 2018
    ## 474   Camion Grande  03 2018
    ## 475   Camion Grande  03 2018
    ## 476   Camion Grande  03 2018
    ## 477           Panel  03 2018
    ## 478  Camion Pequeño  03 2018
    ## 479   Camion Grande  03 2018
    ## 480   Camion Grande  03 2018
    ## 481   Camion Grande  03 2018
    ## 482   Camion Grande  03 2018
    ## 483   Camion Grande  03 2018
    ## 484   Camion Grande  03 2018
    ## 485   Camion Grande  03 2018
    ## 486   Camion Grande  03 2018
    ## 487   Camion Grande  03 2018
    ## 488   Camion Grande  03 2018
    ## 489  Camion Pequeño  03 2018
    ## 490           Panel  03 2018
    ## 491           Panel  03 2018
    ## 492   Camion Grande  03 2018
    ## 493   Camion Grande  03 2018
    ## 494   Camion Grande  03 2018
    ## 495   Camion Grande  03 2018
    ## 496   Camion Grande  03 2018
    ## 497   Camion Grande  03 2018
    ## 498   Camion Grande  03 2018
    ## 499   Camion Grande  03 2018
    ## 500  Camion Pequeño  03 2018
    ## 501   Camion Grande  03 2018
    ## 502           Panel  03 2018
    ## 503   Camion Grande  03 2018
    ## 504   Camion Grande  03 2018
    ## 505  Camion Pequeño  03 2018
    ## 506   Camion Grande  03 2018
    ## 507  Camion Pequeño  03 2018
    ## 508           Panel  03 2018
    ## 509   Camion Grande  03 2018
    ## 510  Camion Pequeño  03 2018
    ## 511   Camion Grande  03 2018
    ## 512   Camion Grande  03 2018
    ## 513   Camion Grande  03 2018
    ## 514   Camion Grande  03 2018
    ## 515   Camion Grande  03 2018
    ## 516  Camion Pequeño  03 2018
    ## 517           Panel  03 2018
    ## 518   Camion Grande  03 2018
    ## 519   Camion Grande  03 2018
    ## 520           Panel  03 2018
    ## 521  Camion Pequeño  03 2018
    ## 522   Camion Grande  03 2018
    ## 523   Camion Grande  03 2018
    ## 524           Panel  03 2018
    ## 525   Camion Grande  03 2018
    ## 526   Camion Grande  03 2018
    ## 527   Camion Grande  03 2018
    ## 528           Panel  03 2018
    ## 529           Panel  03 2018
    ## 530   Camion Grande  03 2018
    ## 531           Panel  03 2018
    ## 532   Camion Grande  03 2018
    ## 533           Panel  03 2018
    ## 534  Camion Pequeño  03 2018
    ## 535   Camion Grande  03 2018
    ## 536           Panel  03 2018
    ## 537   Camion Grande  03 2018
    ## 538   Camion Grande  03 2018
    ## 539  Camion Pequeño  03 2018
    ## 540           Panel  03 2018
    ## 541   Camion Grande  03 2018
    ## 542   Camion Grande  03 2018
    ## 543  Camion Pequeño  03 2018
    ## 544   Camion Grande  03 2018
    ## 545   Camion Grande  03 2018
    ## 546  Camion Pequeño  03 2018
    ## 547  Camion Pequeño  03 2018
    ## 548  Camion Pequeño  03 2018
    ## 549  Camion Pequeño  03 2018
    ## 550  Camion Pequeño  03 2018
    ## 551   Camion Grande  03 2018
    ## 552   Camion Grande  03 2018
    ## 553   Camion Grande  03 2018
    ## 554  Camion Pequeño  03 2018
    ## 555           Panel  03 2018
    ## 556  Camion Pequeño  03 2018
    ## 557   Camion Grande  03 2018
    ## 558  Camion Pequeño  03 2018
    ## 559   Camion Grande  03 2018
    ## 560   Camion Grande  03 2018
    ## 561           Panel  03 2018
    ## 562   Camion Grande  03 2018
    ## 563  Camion Pequeño  03 2018
    ## 564           Panel  03 2018
    ## 565  Camion Pequeño  03 2018
    ## 566  Camion Pequeño  03 2018
    ## 567   Camion Grande  03 2018
    ## 568   Camion Grande  03 2018
    ## 569           Panel  03 2018
    ## 570   Camion Grande  03 2018
    ## 571   Camion Grande  03 2018
    ## 572   Camion Grande  03 2018
    ## 573   Camion Grande  03 2018
    ## 574  Camion Pequeño  03 2018
    ## 575  Camion Pequeño  03 2018
    ## 576  Camion Pequeño  03 2018
    ## 577           Panel  03 2018
    ## 578   Camion Grande  04 2018
    ## 579  Camion Pequeño  04 2018
    ## 580   Camion Grande  04 2018
    ## 581   Camion Grande  04 2018
    ## 582  Camion Pequeño  04 2018
    ## 583  Camion Pequeño  04 2018
    ## 584   Camion Grande  04 2018
    ## 585   Camion Grande  04 2018
    ## 586   Camion Grande  04 2018
    ## 587  Camion Pequeño  04 2018
    ## 588   Camion Grande  04 2018
    ## 589   Camion Grande  04 2018
    ## 590  Camion Pequeño  04 2018
    ## 591   Camion Grande  04 2018
    ## 592  Camion Pequeño  04 2018
    ## 593           Panel  04 2018
    ## 594           Panel  04 2018
    ## 595   Camion Grande  04 2018
    ## 596           Panel  04 2018
    ## 597   Camion Grande  04 2018
    ## 598  Camion Pequeño  04 2018
    ## 599  Camion Pequeño  04 2018
    ## 600  Camion Pequeño  04 2018
    ## 601   Camion Grande  04 2018
    ## 602   Camion Grande  04 2018
    ## 603           Panel  04 2018
    ## 604           Panel  04 2018
    ## 605   Camion Grande  04 2018
    ## 606           Panel  04 2018
    ## 607   Camion Grande  04 2018
    ## 608   Camion Grande  04 2018
    ## 609   Camion Grande  04 2018
    ## 610  Camion Pequeño  04 2018
    ## 611   Camion Grande  04 2018
    ## 612           Panel  04 2018
    ## 613   Camion Grande  04 2018
    ## 614   Camion Grande  04 2018
    ## 615  Camion Pequeño  04 2018
    ## 616   Camion Grande  04 2018
    ## 617   Camion Grande  04 2018
    ## 618           Panel  04 2018
    ## 619  Camion Pequeño  04 2018
    ## 620           Panel  04 2018
    ## 621   Camion Grande  04 2018
    ## 622  Camion Pequeño  04 2018
    ## 623   Camion Grande  04 2018
    ## 624  Camion Pequeño  04 2018
    ## 625   Camion Grande  04 2018
    ## 626   Camion Grande  04 2018
    ## 627           Panel  04 2018
    ## 628   Camion Grande  04 2018
    ## 629           Panel  04 2018
    ## 630   Camion Grande  04 2018
    ## 631   Camion Grande  04 2018
    ## 632   Camion Grande  04 2018
    ## 633   Camion Grande  04 2018
    ## 634   Camion Grande  04 2018
    ## 635   Camion Grande  04 2018
    ## 636   Camion Grande  04 2018
    ## 637   Camion Grande  04 2018
    ## 638  Camion Pequeño  04 2018
    ## 639  Camion Pequeño  04 2018
    ## 640  Camion Pequeño  04 2018
    ## 641  Camion Pequeño  04 2018
    ## 642   Camion Grande  04 2018
    ## 643           Panel  04 2018
    ## 644  Camion Pequeño  04 2018
    ## 645  Camion Pequeño  04 2018
    ## 646   Camion Grande  04 2018
    ## 647           Panel  04 2018
    ## 648   Camion Grande  04 2018
    ## 649   Camion Grande  04 2018
    ## 650   Camion Grande  04 2018
    ## 651  Camion Pequeño  04 2018
    ## 652   Camion Grande  04 2018
    ## 653           Panel  04 2018
    ## 654  Camion Pequeño  04 2018
    ## 655   Camion Grande  04 2018
    ## 656   Camion Grande  04 2018
    ## 657   Camion Grande  04 2018
    ## 658   Camion Grande  04 2018
    ## 659           Panel  04 2018
    ## 660  Camion Pequeño  04 2018
    ## 661   Camion Grande  04 2018
    ## 662           Panel  04 2018
    ## 663  Camion Pequeño  04 2018
    ## 664   Camion Grande  04 2018
    ## 665  Camion Pequeño  04 2018
    ## 666   Camion Grande  04 2018
    ## 667  Camion Pequeño  04 2018
    ## 668   Camion Grande  04 2018
    ## 669   Camion Grande  04 2018
    ## 670   Camion Grande  04 2018
    ## 671           Panel  04 2018
    ## 672  Camion Pequeño  04 2018
    ## 673  Camion Pequeño  04 2018
    ## 674  Camion Pequeño  04 2018
    ## 675  Camion Pequeño  04 2018
    ## 676  Camion Pequeño  04 2018
    ## 677   Camion Grande  04 2018
    ## 678  Camion Pequeño  04 2018
    ## 679   Camion Grande  04 2018
    ## 680  Camion Pequeño  04 2018
    ## 681  Camion Pequeño  04 2018
    ## 682  Camion Pequeño  04 2018
    ## 683   Camion Grande  04 2018
    ## 684           Panel  04 2018
    ## 685  Camion Pequeño  04 2018
    ## 686   Camion Grande  04 2018
    ## 687   Camion Grande  04 2018
    ## 688   Camion Grande  04 2018
    ## 689  Camion Pequeño  04 2018
    ## 690   Camion Grande  04 2018
    ## 691           Panel  04 2018
    ## 692           Panel  04 2018
    ## 693   Camion Grande  04 2018
    ## 694  Camion Pequeño  04 2018
    ## 695   Camion Grande  04 2018
    ## 696   Camion Grande  04 2018
    ## 697   Camion Grande  04 2018
    ## 698           Panel  04 2018
    ## 699           Panel  04 2018
    ## 700  Camion Pequeño  04 2018
    ## 701           Panel  04 2018
    ## 702  Camion Pequeño  04 2018
    ## 703   Camion Grande  04 2018
    ## 704   Camion Grande  04 2018
    ## 705   Camion Grande  04 2018
    ## 706   Camion Grande  04 2018
    ## 707   Camion Grande  04 2018
    ## 708  Camion Pequeño  04 2018
    ## 709  Camion Pequeño  04 2018
    ## 710  Camion Pequeño  04 2018
    ## 711           Panel  04 2018
    ## 712   Camion Grande  04 2018
    ## 713   Camion Grande  04 2018
    ## 714  Camion Pequeño  04 2018
    ## 715   Camion Grande  04 2018
    ## 716  Camion Pequeño  04 2018
    ## 717  Camion Pequeño  04 2018
    ## 718   Camion Grande  04 2018
    ## 719  Camion Pequeño  04 2018
    ## 720   Camion Grande  04 2018
    ## 721   Camion Grande  04 2018
    ## 722   Camion Grande  04 2018
    ## 723           Panel  04 2018
    ## 724   Camion Grande  04 2018
    ## 725   Camion Grande  04 2018
    ## 726   Camion Grande  04 2018
    ## 727  Camion Pequeño  04 2018
    ## 728   Camion Grande  04 2018
    ## 729   Camion Grande  04 2018
    ## 730  Camion Pequeño  04 2018
    ## 731           Panel  04 2018
    ## 732           Panel  04 2018
    ## 733  Camion Pequeño  04 2018
    ## 734  Camion Pequeño  04 2018
    ## 735   Camion Grande  04 2018
    ## 736   Camion Grande  04 2018
    ## 737   Camion Grande  04 2018
    ## 738           Panel  04 2018
    ## 739           Panel  04 2018
    ## 740   Camion Grande  04 2018
    ## 741   Camion Grande  04 2018
    ## 742  Camion Pequeño  04 2018
    ## 743   Camion Grande  04 2018
    ## 744   Camion Grande  04 2018
    ## 745           Panel  04 2018
    ## 746   Camion Grande  04 2018
    ## 747  Camion Pequeño  04 2018
    ## 748   Camion Grande  04 2018
    ## 749  Camion Pequeño  04 2018
    ## 750   Camion Grande  04 2018
    ## 751   Camion Grande  04 2018
    ## 752           Panel  04 2018
    ## 753   Camion Grande  04 2018
    ## 754  Camion Pequeño  04 2018
    ## 755   Camion Grande  04 2018
    ## 756           Panel  04 2018
    ## 757   Camion Grande  04 2018
    ## 758   Camion Grande  04 2018
    ## 759   Camion Grande  04 2018
    ## 760           Panel  04 2018
    ## 761   Camion Grande  04 2018
    ## 762  Camion Pequeño  04 2018
    ## 763   Camion Grande  04 2018
    ## 764   Camion Grande  04 2018
    ## 765           Panel  04 2018
    ## 766   Camion Grande  04 2018
    ## 767  Camion Pequeño  04 2018
    ## 768           Panel  04 2018
    ## 769           Panel  04 2018
    ## 770   Camion Grande  04 2018
    ## 771   Camion Grande  04 2018
    ## 772  Camion Pequeño  04 2018
    ## 773  Camion Pequeño  04 2018
    ## 774  Camion Pequeño  05 2018
    ## 775           Panel  05 2018
    ## 776   Camion Grande  05 2018
    ## 777           Panel  05 2018
    ## 778   Camion Grande  05 2018
    ## 779   Camion Grande  05 2018
    ## 780  Camion Pequeño  05 2018
    ## 781  Camion Pequeño  05 2018
    ## 782           Panel  05 2018
    ## 783  Camion Pequeño  05 2018
    ## 784  Camion Pequeño  05 2018
    ## 785   Camion Grande  05 2018
    ## 786  Camion Pequeño  05 2018
    ## 787   Camion Grande  05 2018
    ## 788           Panel  05 2018
    ## 789  Camion Pequeño  05 2018
    ## 790   Camion Grande  05 2018
    ## 791   Camion Grande  05 2018
    ## 792   Camion Grande  05 2018
    ## 793   Camion Grande  05 2018
    ## 794   Camion Grande  05 2018
    ## 795   Camion Grande  05 2018
    ## 796   Camion Grande  05 2018
    ## 797           Panel  05 2018
    ## 798           Panel  05 2018
    ## 799           Panel  05 2018
    ## 800   Camion Grande  05 2018
    ## 801   Camion Grande  05 2018
    ## 802   Camion Grande  05 2018
    ## 803   Camion Grande  05 2018
    ## 804  Camion Pequeño  05 2018
    ## 805   Camion Grande  05 2018
    ## 806  Camion Pequeño  05 2018
    ## 807   Camion Grande  05 2018
    ## 808           Panel  05 2018
    ## 809  Camion Pequeño  05 2018
    ## 810           Panel  05 2018
    ## 811  Camion Pequeño  05 2018
    ## 812   Camion Grande  05 2018
    ## 813  Camion Pequeño  05 2018
    ## 814  Camion Pequeño  05 2018
    ## 815  Camion Pequeño  05 2018
    ## 816  Camion Pequeño  05 2018
    ## 817   Camion Grande  05 2018
    ## 818  Camion Pequeño  05 2018
    ## 819  Camion Pequeño  05 2018
    ## 820  Camion Pequeño  05 2018
    ## 821   Camion Grande  05 2018
    ## 822  Camion Pequeño  05 2018
    ## 823   Camion Grande  05 2018
    ## 824   Camion Grande  05 2018
    ## 825   Camion Grande  05 2018
    ## 826  Camion Pequeño  05 2018
    ## 827  Camion Pequeño  05 2018
    ## 828   Camion Grande  05 2018
    ## 829   Camion Grande  05 2018
    ## 830  Camion Pequeño  05 2018
    ## 831   Camion Grande  05 2018
    ## 832  Camion Pequeño  05 2018
    ## 833   Camion Grande  05 2018
    ## 834  Camion Pequeño  05 2018
    ## 835   Camion Grande  05 2018
    ## 836   Camion Grande  05 2018
    ## 837   Camion Grande  05 2018
    ## 838  Camion Pequeño  05 2018
    ## 839  Camion Pequeño  05 2018
    ## 840  Camion Pequeño  05 2018
    ## 841           Panel  05 2018
    ## 842   Camion Grande  05 2018
    ## 843   Camion Grande  05 2018
    ## 844   Camion Grande  05 2018
    ## 845   Camion Grande  05 2018
    ## 846  Camion Pequeño  05 2018
    ## 847   Camion Grande  05 2018
    ## 848   Camion Grande  05 2018
    ## 849   Camion Grande  05 2018
    ## 850  Camion Pequeño  05 2018
    ## 851   Camion Grande  05 2018
    ## 852   Camion Grande  05 2018
    ## 853   Camion Grande  05 2018
    ## 854   Camion Grande  05 2018
    ## 855   Camion Grande  05 2018
    ## 856  Camion Pequeño  05 2018
    ## 857   Camion Grande  05 2018
    ## 858           Panel  05 2018
    ## 859   Camion Grande  05 2018
    ## 860   Camion Grande  05 2018
    ## 861   Camion Grande  05 2018
    ## 862   Camion Grande  05 2018
    ## 863   Camion Grande  05 2018
    ## 864           Panel  05 2018
    ## 865  Camion Pequeño  05 2018
    ## 866   Camion Grande  05 2018
    ## 867   Camion Grande  05 2018
    ## 868  Camion Pequeño  05 2018
    ## 869   Camion Grande  05 2018
    ## 870   Camion Grande  05 2018
    ## 871  Camion Pequeño  05 2018
    ## 872   Camion Grande  05 2018
    ## 873   Camion Grande  05 2018
    ## 874  Camion Pequeño  05 2018
    ## 875   Camion Grande  05 2018
    ## 876   Camion Grande  05 2018
    ## 877   Camion Grande  05 2018
    ## 878  Camion Pequeño  05 2018
    ## 879  Camion Pequeño  05 2018
    ## 880   Camion Grande  05 2018
    ## 881   Camion Grande  05 2018
    ## 882           Panel  05 2018
    ## 883   Camion Grande  05 2018
    ## 884   Camion Grande  05 2018
    ## 885  Camion Pequeño  05 2018
    ## 886  Camion Pequeño  05 2018
    ## 887           Panel  05 2018
    ## 888  Camion Pequeño  05 2018
    ## 889  Camion Pequeño  05 2018
    ## 890           Panel  05 2018
    ## 891   Camion Grande  05 2018
    ## 892   Camion Grande  05 2018
    ## 893  Camion Pequeño  05 2018
    ## 894   Camion Grande  05 2018
    ## 895   Camion Grande  05 2018
    ## 896  Camion Pequeño  05 2018
    ## 897   Camion Grande  05 2018
    ## 898   Camion Grande  05 2018
    ## 899  Camion Pequeño  05 2018
    ## 900   Camion Grande  05 2018
    ## 901   Camion Grande  05 2018
    ## 902  Camion Pequeño  05 2018
    ## 903           Panel  05 2018
    ## 904  Camion Pequeño  05 2018
    ## 905  Camion Pequeño  05 2018
    ## 906  Camion Pequeño  05 2018
    ## 907  Camion Pequeño  05 2018
    ## 908  Camion Pequeño  05 2018
    ## 909   Camion Grande  05 2018
    ## 910  Camion Pequeño  05 2018
    ## 911   Camion Grande  05 2018
    ## 912   Camion Grande  05 2018
    ## 913   Camion Grande  05 2018
    ## 914   Camion Grande  05 2018
    ## 915   Camion Grande  05 2018
    ## 916           Panel  05 2018
    ## 917   Camion Grande  05 2018
    ## 918           Panel  05 2018
    ## 919   Camion Grande  05 2018
    ## 920  Camion Pequeño  05 2018
    ## 921   Camion Grande  05 2018
    ## 922           Panel  05 2018
    ## 923           Panel  05 2018
    ## 924  Camion Pequeño  05 2018
    ## 925   Camion Grande  05 2018
    ## 926   Camion Grande  05 2018
    ## 927           Panel  05 2018
    ## 928           Panel  05 2018
    ## 929   Camion Grande  05 2018
    ## 930  Camion Pequeño  05 2018
    ## 931   Camion Grande  05 2018
    ## 932   Camion Grande  05 2018
    ## 933  Camion Pequeño  05 2018
    ## 934   Camion Grande  05 2018
    ## 935  Camion Pequeño  05 2018
    ## 936  Camion Pequeño  05 2018
    ## 937   Camion Grande  05 2018
    ## 938   Camion Grande  05 2018
    ## 939  Camion Pequeño  05 2018
    ## 940  Camion Pequeño  05 2018
    ## 941   Camion Grande  05 2018
    ## 942   Camion Grande  05 2018
    ## 943   Camion Grande  05 2018
    ## 944  Camion Pequeño  05 2018
    ## 945  Camion Pequeño  05 2018
    ## 946   Camion Grande  05 2018
    ## 947   Camion Grande  05 2018
    ## 948   Camion Grande  05 2018
    ## 949   Camion Grande  05 2018
    ## 950           Panel  05 2018
    ## 951   Camion Grande  05 2018
    ## 952  Camion Pequeño  05 2018
    ## 953   Camion Grande  05 2018
    ## 954   Camion Grande  05 2018
    ## 955           Panel  05 2018
    ## 956   Camion Grande  05 2018
    ## 957  Camion Pequeño  05 2018
    ## 958   Camion Grande  05 2018
    ## 959   Camion Grande  05 2018
    ## 960   Camion Grande  05 2018
    ## 961  Camion Pequeño  05 2018
    ## 962   Camion Grande  05 2018
    ## 963  Camion Pequeño  05 2018
    ## 964  Camion Pequeño  05 2018
    ## 965   Camion Grande  05 2018
    ## 966   Camion Grande  05 2018
    ## 967   Camion Grande  05 2018
    ## 968   Camion Grande  05 2018
    ## 969  Camion Pequeño  05 2018
    ## 970   Camion Grande  05 2018
    ## 971  Camion Pequeño  05 2018
    ## 972  Camion Pequeño  05 2018
    ## 973   Camion Grande  05 2018
    ## 974           Panel  05 2018
    ## 975           Panel  05 2018
    ## 976   Camion Grande  05 2018
    ## 977   Camion Grande  05 2018
    ## 978   Camion Grande  05 2018
    ## 979  Camion Pequeño  05 2018
    ## 980   Camion Grande  05 2018
    ## 981  Camion Pequeño  05 2018
    ## 982  Camion Pequeño  05 2018
    ## 983   Camion Grande  05 2018
    ## 984   Camion Grande  05 2018
    ## 985   Camion Grande  05 2018
    ## 986   Camion Grande  05 2018
    ## 987  Camion Pequeño  05 2018
    ## 988   Camion Grande  05 2018
    ## 989   Camion Grande  06 2018
    ## 990           Panel  06 2018
    ## 991   Camion Grande  06 2018
    ## 992   Camion Grande  06 2018
    ## 993   Camion Grande  06 2018
    ## 994   Camion Grande  06 2018
    ## 995           Panel  06 2018
    ## 996   Camion Grande  06 2018
    ## 997  Camion Pequeño  06 2018
    ## 998   Camion Grande  06 2018
    ## 999   Camion Grande  06 2018
    ## 1000  Camion Grande  06 2018
    ## 1001  Camion Grande  06 2018
    ## 1002          Panel  06 2018
    ## 1003          Panel  06 2018
    ## 1004          Panel  06 2018
    ## 1005  Camion Grande  06 2018
    ## 1006  Camion Grande  06 2018
    ## 1007          Panel  06 2018
    ## 1008  Camion Grande  06 2018
    ## 1009  Camion Grande  06 2018
    ## 1010  Camion Grande  06 2018
    ## 1011          Panel  06 2018
    ## 1012  Camion Grande  06 2018
    ## 1013 Camion Pequeño  06 2018
    ## 1014  Camion Grande  06 2018
    ## 1015          Panel  06 2018
    ## 1016 Camion Pequeño  06 2018
    ## 1017          Panel  06 2018
    ## 1018 Camion Pequeño  06 2018
    ## 1019  Camion Grande  06 2018
    ## 1020  Camion Grande  06 2018
    ## 1021  Camion Grande  06 2018
    ## 1022  Camion Grande  06 2018
    ## 1023          Panel  06 2018
    ## 1024  Camion Grande  06 2018
    ## 1025 Camion Pequeño  06 2018
    ## 1026  Camion Grande  06 2018
    ## 1027  Camion Grande  06 2018
    ## 1028  Camion Grande  06 2018
    ## 1029  Camion Grande  06 2018
    ## 1030  Camion Grande  06 2018
    ## 1031  Camion Grande  06 2018
    ## 1032  Camion Grande  06 2018
    ## 1033  Camion Grande  06 2018
    ## 1034 Camion Pequeño  06 2018
    ## 1035          Panel  06 2018
    ## 1036  Camion Grande  06 2018
    ## 1037 Camion Pequeño  06 2018
    ## 1038  Camion Grande  06 2018
    ## 1039  Camion Grande  06 2018
    ## 1040          Panel  06 2018
    ## 1041  Camion Grande  06 2018
    ## 1042 Camion Pequeño  06 2018
    ## 1043 Camion Pequeño  06 2018
    ## 1044 Camion Pequeño  06 2018
    ## 1045 Camion Pequeño  06 2018
    ## 1046  Camion Grande  06 2018
    ## 1047  Camion Grande  06 2018
    ## 1048          Panel  06 2018
    ## 1049          Panel  06 2018
    ## 1050  Camion Grande  06 2018
    ## 1051  Camion Grande  06 2018
    ## 1052  Camion Grande  06 2018
    ## 1053 Camion Pequeño  06 2018
    ## 1054 Camion Pequeño  06 2018
    ## 1055 Camion Pequeño  06 2018
    ## 1056  Camion Grande  06 2018
    ## 1057          Panel  06 2018
    ## 1058 Camion Pequeño  06 2018
    ## 1059 Camion Pequeño  06 2018
    ## 1060 Camion Pequeño  06 2018
    ## 1061  Camion Grande  06 2018
    ## 1062  Camion Grande  06 2018
    ## 1063  Camion Grande  06 2018
    ## 1064  Camion Grande  06 2018
    ## 1065  Camion Grande  06 2018
    ## 1066  Camion Grande  06 2018
    ## 1067  Camion Grande  06 2018
    ## 1068  Camion Grande  06 2018
    ## 1069  Camion Grande  06 2018
    ## 1070  Camion Grande  06 2018
    ## 1071          Panel  06 2018
    ## 1072  Camion Grande  06 2018
    ## 1073 Camion Pequeño  06 2018
    ## 1074  Camion Grande  06 2018
    ## 1075  Camion Grande  06 2018
    ## 1076  Camion Grande  06 2018
    ## 1077  Camion Grande  06 2018
    ## 1078  Camion Grande  06 2018
    ## 1079 Camion Pequeño  06 2018
    ## 1080 Camion Pequeño  06 2018
    ## 1081  Camion Grande  06 2018
    ## 1082          Panel  06 2018
    ## 1083  Camion Grande  06 2018
    ## 1084          Panel  06 2018
    ## 1085  Camion Grande  06 2018
    ## 1086          Panel  06 2018
    ## 1087          Panel  06 2018
    ## 1088 Camion Pequeño  06 2018
    ## 1089 Camion Pequeño  06 2018
    ## 1090          Panel  06 2018
    ## 1091  Camion Grande  06 2018
    ## 1092 Camion Pequeño  06 2018
    ## 1093  Camion Grande  06 2018
    ## 1094 Camion Pequeño  06 2018
    ## 1095  Camion Grande  06 2018
    ## 1096  Camion Grande  06 2018
    ## 1097          Panel  06 2018
    ## 1098 Camion Pequeño  06 2018
    ## 1099  Camion Grande  06 2018
    ## 1100  Camion Grande  06 2018
    ## 1101 Camion Pequeño  06 2018
    ## 1102  Camion Grande  06 2018
    ## 1103 Camion Pequeño  06 2018
    ## 1104 Camion Pequeño  06 2018
    ## 1105 Camion Pequeño  06 2018
    ## 1106  Camion Grande  06 2018
    ## 1107  Camion Grande  06 2018
    ## 1108 Camion Pequeño  06 2018
    ## 1109  Camion Grande  06 2018
    ## 1110  Camion Grande  06 2018
    ## 1111  Camion Grande  06 2018
    ## 1112  Camion Grande  06 2018
    ## 1113  Camion Grande  06 2018
    ## 1114  Camion Grande  06 2018
    ## 1115 Camion Pequeño  06 2018
    ## 1116 Camion Pequeño  06 2018
    ## 1117 Camion Pequeño  06 2018
    ## 1118  Camion Grande  06 2018
    ## 1119          Panel  06 2018
    ## 1120 Camion Pequeño  06 2018
    ## 1121          Panel  06 2018
    ## 1122  Camion Grande  06 2018
    ## 1123  Camion Grande  06 2018
    ## 1124  Camion Grande  06 2018
    ## 1125 Camion Pequeño  06 2018
    ## 1126  Camion Grande  06 2018
    ## 1127  Camion Grande  06 2018
    ## 1128          Panel  06 2018
    ## 1129          Panel  06 2018
    ## 1130  Camion Grande  06 2018
    ## 1131  Camion Grande  06 2018
    ## 1132          Panel  06 2018
    ## 1133  Camion Grande  06 2018
    ## 1134 Camion Pequeño  06 2018
    ## 1135  Camion Grande  06 2018
    ## 1136          Panel  06 2018
    ## 1137          Panel  06 2018
    ## 1138          Panel  06 2018
    ## 1139  Camion Grande  06 2018
    ## 1140  Camion Grande  06 2018
    ## 1141          Panel  06 2018
    ## 1142  Camion Grande  06 2018
    ## 1143 Camion Pequeño  06 2018
    ## 1144  Camion Grande  06 2018
    ## 1145  Camion Grande  06 2018
    ## 1146 Camion Pequeño  06 2018
    ## 1147  Camion Grande  06 2018
    ## 1148  Camion Grande  06 2018
    ## 1149  Camion Grande  06 2018
    ## 1150  Camion Grande  06 2018
    ## 1151 Camion Pequeño  06 2018
    ## 1152  Camion Grande  06 2018
    ## 1153 Camion Pequeño  06 2018
    ## 1154 Camion Pequeño  06 2018
    ## 1155  Camion Grande  06 2018
    ## 1156          Panel  06 2018
    ## 1157          Panel  06 2018
    ## 1158  Camion Grande  06 2018
    ## 1159 Camion Pequeño  06 2018
    ## 1160 Camion Pequeño  06 2018
    ## 1161  Camion Grande  06 2018
    ## 1162 Camion Pequeño  06 2018
    ## 1163          Panel  06 2018
    ## 1164 Camion Pequeño  06 2018
    ## 1165 Camion Pequeño  06 2018
    ## 1166          Panel  06 2018
    ## 1167 Camion Pequeño  06 2018
    ## 1168  Camion Grande  06 2018
    ## 1169 Camion Pequeño  06 2018
    ## 1170  Camion Grande  06 2018
    ## 1171  Camion Grande  06 2018
    ## 1172  Camion Grande  06 2018
    ## 1173          Panel  06 2018
    ## 1174          Panel  06 2018
    ## 1175  Camion Grande  06 2018
    ## 1176  Camion Grande  06 2018
    ## 1177          Panel  06 2018
    ## 1178 Camion Pequeño  06 2018
    ## 1179          Panel  06 2018
    ## 1180  Camion Grande  06 2018
    ## 1181  Camion Grande  06 2018
    ## 1182  Camion Grande  06 2018
    ## 1183  Camion Grande  06 2018
    ## 1184          Panel  06 2018
    ## 1185 Camion Pequeño  06 2018
    ## 1186  Camion Grande  07 2018
    ## 1187  Camion Grande  07 2018
    ## 1188 Camion Pequeño  07 2018
    ## 1189  Camion Grande  07 2018
    ## 1190  Camion Grande  07 2018
    ## 1191          Panel  07 2018
    ## 1192  Camion Grande  07 2018
    ## 1193 Camion Pequeño  07 2018
    ## 1194  Camion Grande  07 2018
    ## 1195          Panel  07 2018
    ## 1196          Panel  07 2018
    ## 1197 Camion Pequeño  07 2018
    ## 1198 Camion Pequeño  07 2018
    ## 1199          Panel  07 2018
    ## 1200  Camion Grande  07 2018
    ## 1201          Panel  07 2018
    ## 1202 Camion Pequeño  07 2018
    ## 1203  Camion Grande  07 2018
    ## 1204  Camion Grande  07 2018
    ## 1205 Camion Pequeño  07 2018
    ## 1206  Camion Grande  07 2018
    ## 1207  Camion Grande  07 2018
    ## 1208 Camion Pequeño  07 2018
    ## 1209  Camion Grande  07 2018
    ## 1210  Camion Grande  07 2018
    ## 1211  Camion Grande  07 2018
    ## 1212          Panel  07 2018
    ## 1213          Panel  07 2018
    ## 1214  Camion Grande  07 2018
    ## 1215 Camion Pequeño  07 2018
    ## 1216  Camion Grande  07 2018
    ## 1217  Camion Grande  07 2018
    ## 1218  Camion Grande  07 2018
    ## 1219  Camion Grande  07 2018
    ## 1220  Camion Grande  07 2018
    ## 1221          Panel  07 2018
    ## 1222  Camion Grande  07 2018
    ## 1223 Camion Pequeño  07 2018
    ## 1224  Camion Grande  07 2018
    ## 1225  Camion Grande  07 2018
    ## 1226  Camion Grande  07 2018
    ## 1227 Camion Pequeño  07 2018
    ## 1228  Camion Grande  07 2018
    ## 1229 Camion Pequeño  07 2018
    ## 1230          Panel  07 2018
    ## 1231          Panel  07 2018
    ## 1232 Camion Pequeño  07 2018
    ## 1233  Camion Grande  07 2018
    ## 1234  Camion Grande  07 2018
    ## 1235 Camion Pequeño  07 2018
    ## 1236  Camion Grande  07 2018
    ## 1237 Camion Pequeño  07 2018
    ## 1238  Camion Grande  07 2018
    ## 1239  Camion Grande  07 2018
    ## 1240  Camion Grande  07 2018
    ## 1241          Panel  07 2018
    ## 1242  Camion Grande  07 2018
    ## 1243  Camion Grande  07 2018
    ## 1244          Panel  07 2018
    ## 1245 Camion Pequeño  07 2018
    ## 1246 Camion Pequeño  07 2018
    ## 1247  Camion Grande  07 2018
    ## 1248 Camion Pequeño  07 2018
    ## 1249  Camion Grande  07 2018
    ## 1250 Camion Pequeño  07 2018
    ## 1251  Camion Grande  07 2018
    ## 1252  Camion Grande  07 2018
    ## 1253 Camion Pequeño  07 2018
    ## 1254  Camion Grande  07 2018
    ## 1255  Camion Grande  07 2018
    ## 1256  Camion Grande  07 2018
    ## 1257  Camion Grande  07 2018
    ## 1258  Camion Grande  07 2018
    ## 1259 Camion Pequeño  07 2018
    ## 1260  Camion Grande  07 2018
    ## 1261  Camion Grande  07 2018
    ## 1262  Camion Grande  07 2018
    ## 1263  Camion Grande  07 2018
    ## 1264 Camion Pequeño  07 2018
    ## 1265  Camion Grande  07 2018
    ## 1266  Camion Grande  07 2018
    ## 1267  Camion Grande  07 2018
    ## 1268  Camion Grande  07 2018
    ## 1269  Camion Grande  07 2018
    ## 1270  Camion Grande  07 2018
    ## 1271  Camion Grande  07 2018
    ## 1272 Camion Pequeño  07 2018
    ## 1273          Panel  07 2018
    ## 1274  Camion Grande  07 2018
    ## 1275          Panel  07 2018
    ## 1276          Panel  07 2018
    ## 1277  Camion Grande  07 2018
    ## 1278  Camion Grande  07 2018
    ## 1279  Camion Grande  07 2018
    ## 1280          Panel  07 2018
    ## 1281          Panel  07 2018
    ## 1282  Camion Grande  07 2018
    ## 1283  Camion Grande  07 2018
    ## 1284  Camion Grande  07 2018
    ## 1285  Camion Grande  07 2018
    ## 1286  Camion Grande  07 2018
    ## 1287          Panel  07 2018
    ## 1288  Camion Grande  07 2018
    ## 1289  Camion Grande  07 2018
    ## 1290  Camion Grande  07 2018
    ## 1291          Panel  07 2018
    ## 1292 Camion Pequeño  07 2018
    ## 1293  Camion Grande  07 2018
    ## 1294 Camion Pequeño  07 2018
    ## 1295  Camion Grande  07 2018
    ## 1296  Camion Grande  07 2018
    ## 1297          Panel  07 2018
    ## 1298  Camion Grande  07 2018
    ## 1299 Camion Pequeño  07 2018
    ## 1300  Camion Grande  07 2018
    ## 1301  Camion Grande  07 2018
    ## 1302  Camion Grande  07 2018
    ## 1303  Camion Grande  07 2018
    ## 1304  Camion Grande  07 2018
    ## 1305 Camion Pequeño  07 2018
    ## 1306 Camion Pequeño  07 2018
    ## 1307 Camion Pequeño  07 2018
    ## 1308  Camion Grande  07 2018
    ## 1309  Camion Grande  07 2018
    ## 1310  Camion Grande  07 2018
    ## 1311 Camion Pequeño  07 2018
    ## 1312          Panel  07 2018
    ## 1313  Camion Grande  07 2018
    ## 1314  Camion Grande  07 2018
    ## 1315  Camion Grande  07 2018
    ## 1316          Panel  07 2018
    ## 1317 Camion Pequeño  07 2018
    ## 1318  Camion Grande  07 2018
    ## 1319          Panel  07 2018
    ## 1320  Camion Grande  07 2018
    ## 1321  Camion Grande  07 2018
    ## 1322  Camion Grande  07 2018
    ## 1323 Camion Pequeño  07 2018
    ## 1324  Camion Grande  07 2018
    ## 1325 Camion Pequeño  07 2018
    ## 1326 Camion Pequeño  07 2018
    ## 1327  Camion Grande  07 2018
    ## 1328 Camion Pequeño  07 2018
    ## 1329          Panel  07 2018
    ## 1330  Camion Grande  07 2018
    ## 1331  Camion Grande  07 2018
    ## 1332  Camion Grande  07 2018
    ## 1333  Camion Grande  07 2018
    ## 1334  Camion Grande  07 2018
    ## 1335  Camion Grande  07 2018
    ## 1336  Camion Grande  07 2018
    ## 1337          Panel  07 2018
    ## 1338          Panel  07 2018
    ## 1339 Camion Pequeño  07 2018
    ## 1340          Panel  07 2018
    ## 1341  Camion Grande  07 2018
    ## 1342  Camion Grande  07 2018
    ## 1343 Camion Pequeño  07 2018
    ## 1344          Panel  07 2018
    ## 1345 Camion Pequeño  07 2018
    ## 1346  Camion Grande  07 2018
    ## 1347  Camion Grande  07 2018
    ## 1348  Camion Grande  07 2018
    ## 1349  Camion Grande  07 2018
    ## 1350 Camion Pequeño  07 2018
    ## 1351          Panel  07 2018
    ## 1352  Camion Grande  07 2018
    ## 1353          Panel  07 2018
    ## 1354          Panel  07 2018
    ## 1355 Camion Pequeño  07 2018
    ## 1356 Camion Pequeño  07 2018
    ## 1357 Camion Pequeño  07 2018
    ## 1358  Camion Grande  07 2018
    ## 1359          Panel  07 2018
    ## 1360 Camion Pequeño  07 2018
    ## 1361  Camion Grande  07 2018
    ## 1362 Camion Pequeño  07 2018
    ## 1363  Camion Grande  07 2018
    ## 1364  Camion Grande  07 2018
    ## 1365  Camion Grande  07 2018
    ## 1366  Camion Grande  07 2018
    ## 1367  Camion Grande  07 2018
    ## 1368          Panel  07 2018
    ## 1369  Camion Grande  07 2018
    ## 1370          Panel  07 2018
    ## 1371 Camion Pequeño  07 2018
    ## 1372  Camion Grande  07 2018
    ## 1373 Camion Pequeño  07 2018
    ## 1374          Panel  07 2018
    ## 1375          Panel  07 2018
    ## 1376          Panel  07 2018
    ## 1377  Camion Grande  07 2018
    ## 1378  Camion Grande  07 2018
    ## 1379  Camion Grande  07 2018
    ## 1380  Camion Grande  07 2018
    ## 1381          Panel  07 2018
    ## 1382  Camion Grande  07 2018
    ## 1383          Panel  07 2018
    ## 1384  Camion Grande  07 2018
    ## 1385 Camion Pequeño  07 2018
    ## 1386 Camion Pequeño  07 2018
    ## 1387  Camion Grande  07 2018
    ## 1388  Camion Grande  07 2018
    ## 1389  Camion Grande  07 2018
    ## 1390  Camion Grande  07 2018
    ## 1391  Camion Grande  07 2018
    ## 1392  Camion Grande  07 2018
    ## 1393          Panel  07 2018
    ## 1394 Camion Pequeño  07 2018
    ## 1395 Camion Pequeño  07 2018
    ## 1396          Panel  07 2018
    ## 1397  Camion Grande  08 2018
    ## 1398 Camion Pequeño  08 2018
    ## 1399 Camion Pequeño  08 2018
    ## 1400  Camion Grande  08 2018
    ## 1401 Camion Pequeño  08 2018
    ## 1402  Camion Grande  08 2018
    ## 1403 Camion Pequeño  08 2018
    ## 1404  Camion Grande  08 2018
    ## 1405  Camion Grande  08 2018
    ## 1406  Camion Grande  08 2018
    ## 1407          Panel  08 2018
    ## 1408          Panel  08 2018
    ## 1409  Camion Grande  08 2018
    ## 1410  Camion Grande  08 2018
    ## 1411  Camion Grande  08 2018
    ## 1412  Camion Grande  08 2018
    ## 1413 Camion Pequeño  08 2018
    ## 1414  Camion Grande  08 2018
    ## 1415          Panel  08 2018
    ## 1416          Panel  08 2018
    ## 1417          Panel  08 2018
    ## 1418  Camion Grande  08 2018
    ## 1419  Camion Grande  08 2018
    ## 1420  Camion Grande  08 2018
    ## 1421  Camion Grande  08 2018
    ## 1422 Camion Pequeño  08 2018
    ## 1423  Camion Grande  08 2018
    ## 1424  Camion Grande  08 2018
    ## 1425  Camion Grande  08 2018
    ## 1426          Panel  08 2018
    ## 1427  Camion Grande  08 2018
    ## 1428          Panel  08 2018
    ## 1429  Camion Grande  08 2018
    ## 1430          Panel  08 2018
    ## 1431  Camion Grande  08 2018
    ## 1432 Camion Pequeño  08 2018
    ## 1433  Camion Grande  08 2018
    ## 1434  Camion Grande  08 2018
    ## 1435  Camion Grande  08 2018
    ## 1436 Camion Pequeño  08 2018
    ## 1437          Panel  08 2018
    ## 1438 Camion Pequeño  08 2018
    ## 1439  Camion Grande  08 2018
    ## 1440          Panel  08 2018
    ## 1441          Panel  08 2018
    ## 1442  Camion Grande  08 2018
    ## 1443  Camion Grande  08 2018
    ## 1444 Camion Pequeño  08 2018
    ## 1445 Camion Pequeño  08 2018
    ## 1446  Camion Grande  08 2018
    ## 1447  Camion Grande  08 2018
    ## 1448 Camion Pequeño  08 2018
    ## 1449  Camion Grande  08 2018
    ## 1450  Camion Grande  08 2018
    ## 1451  Camion Grande  08 2018
    ## 1452  Camion Grande  08 2018
    ## 1453 Camion Pequeño  08 2018
    ## 1454  Camion Grande  08 2018
    ## 1455 Camion Pequeño  08 2018
    ## 1456  Camion Grande  08 2018
    ## 1457 Camion Pequeño  08 2018
    ## 1458  Camion Grande  08 2018
    ## 1459 Camion Pequeño  08 2018
    ## 1460  Camion Grande  08 2018
    ## 1461  Camion Grande  08 2018
    ## 1462  Camion Grande  08 2018
    ## 1463          Panel  08 2018
    ## 1464 Camion Pequeño  08 2018
    ## 1465  Camion Grande  08 2018
    ## 1466          Panel  08 2018
    ## 1467  Camion Grande  08 2018
    ## 1468  Camion Grande  08 2018
    ## 1469  Camion Grande  08 2018
    ## 1470 Camion Pequeño  08 2018
    ## 1471  Camion Grande  08 2018
    ## 1472 Camion Pequeño  08 2018
    ## 1473 Camion Pequeño  08 2018
    ## 1474  Camion Grande  08 2018
    ## 1475          Panel  08 2018
    ## 1476  Camion Grande  08 2018
    ## 1477  Camion Grande  08 2018
    ## 1478 Camion Pequeño  08 2018
    ## 1479 Camion Pequeño  08 2018
    ## 1480 Camion Pequeño  08 2018
    ## 1481 Camion Pequeño  08 2018
    ## 1482  Camion Grande  08 2018
    ## 1483 Camion Pequeño  08 2018
    ## 1484 Camion Pequeño  08 2018
    ## 1485          Panel  08 2018
    ## 1486 Camion Pequeño  08 2018
    ## 1487  Camion Grande  08 2018
    ## 1488 Camion Pequeño  08 2018
    ## 1489          Panel  08 2018
    ## 1490 Camion Pequeño  08 2018
    ## 1491  Camion Grande  08 2018
    ## 1492 Camion Pequeño  08 2018
    ## 1493 Camion Pequeño  08 2018
    ## 1494          Panel  08 2018
    ## 1495  Camion Grande  08 2018
    ## 1496  Camion Grande  08 2018
    ## 1497  Camion Grande  08 2018
    ## 1498          Panel  08 2018
    ## 1499          Panel  08 2018
    ## 1500  Camion Grande  08 2018
    ## 1501          Panel  08 2018
    ## 1502  Camion Grande  08 2018
    ## 1503  Camion Grande  08 2018
    ## 1504  Camion Grande  08 2018
    ## 1505  Camion Grande  08 2018
    ## 1506  Camion Grande  08 2018
    ## 1507  Camion Grande  08 2018
    ## 1508 Camion Pequeño  08 2018
    ## 1509          Panel  08 2018
    ## 1510  Camion Grande  08 2018
    ## 1511          Panel  08 2018
    ## 1512 Camion Pequeño  08 2018
    ## 1513          Panel  08 2018
    ## 1514  Camion Grande  08 2018
    ## 1515  Camion Grande  08 2018
    ## 1516 Camion Pequeño  08 2018
    ## 1517  Camion Grande  08 2018
    ## 1518 Camion Pequeño  08 2018
    ## 1519  Camion Grande  08 2018
    ## 1520  Camion Grande  08 2018
    ## 1521  Camion Grande  08 2018
    ## 1522 Camion Pequeño  08 2018
    ## 1523          Panel  08 2018
    ## 1524  Camion Grande  08 2018
    ## 1525  Camion Grande  08 2018
    ## 1526  Camion Grande  08 2018
    ## 1527          Panel  08 2018
    ## 1528 Camion Pequeño  08 2018
    ## 1529 Camion Pequeño  08 2018
    ## 1530          Panel  08 2018
    ## 1531  Camion Grande  08 2018
    ## 1532  Camion Grande  08 2018
    ## 1533  Camion Grande  08 2018
    ## 1534          Panel  08 2018
    ## 1535 Camion Pequeño  08 2018
    ## 1536 Camion Pequeño  08 2018
    ## 1537 Camion Pequeño  08 2018
    ## 1538  Camion Grande  08 2018
    ## 1539  Camion Grande  08 2018
    ## 1540 Camion Pequeño  08 2018
    ## 1541  Camion Grande  08 2018
    ## 1542 Camion Pequeño  08 2018
    ## 1543 Camion Pequeño  08 2018
    ## 1544 Camion Pequeño  08 2018
    ## 1545 Camion Pequeño  08 2018
    ## 1546 Camion Pequeño  08 2018
    ## 1547  Camion Grande  08 2018
    ## 1548  Camion Grande  08 2018
    ## 1549  Camion Grande  08 2018
    ## 1550  Camion Grande  08 2018
    ## 1551 Camion Pequeño  08 2018
    ## 1552 Camion Pequeño  08 2018
    ## 1553  Camion Grande  08 2018
    ## 1554          Panel  08 2018
    ## 1555  Camion Grande  08 2018
    ## 1556 Camion Pequeño  08 2018
    ## 1557 Camion Pequeño  08 2018
    ## 1558 Camion Pequeño  08 2018
    ## 1559 Camion Pequeño  08 2018
    ## 1560  Camion Grande  08 2018
    ## 1561 Camion Pequeño  08 2018
    ## 1562          Panel  08 2018
    ## 1563 Camion Pequeño  08 2018
    ## 1564          Panel  08 2018
    ## 1565  Camion Grande  08 2018
    ## 1566          Panel  08 2018
    ## 1567  Camion Grande  08 2018
    ## 1568  Camion Grande  08 2018
    ## 1569  Camion Grande  08 2018
    ## 1570  Camion Grande  08 2018
    ## 1571  Camion Grande  08 2018
    ## 1572  Camion Grande  08 2018
    ## 1573 Camion Pequeño  08 2018
    ## 1574          Panel  08 2018
    ## 1575  Camion Grande  08 2018
    ## 1576 Camion Pequeño  08 2018
    ## 1577  Camion Grande  08 2018
    ## 1578          Panel  08 2018
    ## 1579  Camion Grande  08 2018
    ## 1580 Camion Pequeño  08 2018
    ## 1581          Panel  08 2018
    ## 1582 Camion Pequeño  08 2018
    ## 1583  Camion Grande  08 2018
    ## 1584  Camion Grande  08 2018
    ## 1585 Camion Pequeño  08 2018
    ## 1586  Camion Grande  08 2018
    ## 1587  Camion Grande  08 2018
    ## 1588  Camion Grande  08 2018
    ## 1589          Panel  08 2018
    ## 1590  Camion Grande  08 2018
    ## 1591  Camion Grande  08 2018
    ## 1592  Camion Grande  08 2018
    ## 1593 Camion Pequeño  08 2018
    ## 1594  Camion Grande  08 2018
    ## 1595 Camion Pequeño  08 2018
    ## 1596  Camion Grande  09 2018
    ## 1597  Camion Grande  09 2018
    ## 1598  Camion Grande  09 2018
    ## 1599  Camion Grande  09 2018
    ## 1600  Camion Grande  09 2018
    ## 1601 Camion Pequeño  09 2018
    ## 1602  Camion Grande  09 2018
    ## 1603 Camion Pequeño  09 2018
    ## 1604 Camion Pequeño  09 2018
    ## 1605 Camion Pequeño  09 2018
    ## 1606  Camion Grande  09 2018
    ## 1607 Camion Pequeño  09 2018
    ## 1608  Camion Grande  09 2018
    ## 1609 Camion Pequeño  09 2018
    ## 1610  Camion Grande  09 2018
    ## 1611  Camion Grande  09 2018
    ## 1612  Camion Grande  09 2018
    ## 1613  Camion Grande  09 2018
    ## 1614 Camion Pequeño  09 2018
    ## 1615 Camion Pequeño  09 2018
    ## 1616          Panel  09 2018
    ## 1617  Camion Grande  09 2018
    ## 1618  Camion Grande  09 2018
    ## 1619  Camion Grande  09 2018
    ## 1620  Camion Grande  09 2018
    ## 1621 Camion Pequeño  09 2018
    ## 1622 Camion Pequeño  09 2018
    ## 1623  Camion Grande  09 2018
    ## 1624  Camion Grande  09 2018
    ## 1625          Panel  09 2018
    ## 1626  Camion Grande  09 2018
    ## 1627  Camion Grande  09 2018
    ## 1628  Camion Grande  09 2018
    ## 1629  Camion Grande  09 2018
    ## 1630          Panel  09 2018
    ## 1631          Panel  09 2018
    ## 1632          Panel  09 2018
    ## 1633          Panel  09 2018
    ## 1634          Panel  09 2018
    ## 1635          Panel  09 2018
    ## 1636 Camion Pequeño  09 2018
    ## 1637  Camion Grande  09 2018
    ## 1638  Camion Grande  09 2018
    ## 1639  Camion Grande  09 2018
    ## 1640  Camion Grande  09 2018
    ## 1641  Camion Grande  09 2018
    ## 1642 Camion Pequeño  09 2018
    ## 1643  Camion Grande  09 2018
    ## 1644  Camion Grande  09 2018
    ## 1645 Camion Pequeño  09 2018
    ## 1646  Camion Grande  09 2018
    ## 1647 Camion Pequeño  09 2018
    ## 1648          Panel  09 2018
    ## 1649          Panel  09 2018
    ## 1650  Camion Grande  09 2018
    ## 1651 Camion Pequeño  09 2018
    ## 1652          Panel  09 2018
    ## 1653  Camion Grande  09 2018
    ## 1654  Camion Grande  09 2018
    ## 1655 Camion Pequeño  09 2018
    ## 1656 Camion Pequeño  09 2018
    ## 1657 Camion Pequeño  09 2018
    ## 1658          Panel  09 2018
    ## 1659  Camion Grande  09 2018
    ## 1660 Camion Pequeño  09 2018
    ## 1661 Camion Pequeño  09 2018
    ## 1662 Camion Pequeño  09 2018
    ## 1663  Camion Grande  09 2018
    ## 1664 Camion Pequeño  09 2018
    ## 1665          Panel  09 2018
    ## 1666 Camion Pequeño  09 2018
    ## 1667          Panel  09 2018
    ## 1668  Camion Grande  09 2018
    ## 1669  Camion Grande  09 2018
    ## 1670  Camion Grande  09 2018
    ## 1671  Camion Grande  09 2018
    ## 1672  Camion Grande  09 2018
    ## 1673 Camion Pequeño  09 2018
    ## 1674  Camion Grande  09 2018
    ## 1675  Camion Grande  09 2018
    ## 1676  Camion Grande  09 2018
    ## 1677 Camion Pequeño  09 2018
    ## 1678          Panel  09 2018
    ## 1679  Camion Grande  09 2018
    ## 1680  Camion Grande  09 2018
    ## 1681          Panel  09 2018
    ## 1682 Camion Pequeño  09 2018
    ## 1683  Camion Grande  09 2018
    ## 1684  Camion Grande  09 2018
    ## 1685  Camion Grande  09 2018
    ## 1686 Camion Pequeño  09 2018
    ## 1687  Camion Grande  09 2018
    ## 1688 Camion Pequeño  09 2018
    ## 1689          Panel  09 2018
    ## 1690  Camion Grande  09 2018
    ## 1691  Camion Grande  09 2018
    ## 1692  Camion Grande  09 2018
    ## 1693  Camion Grande  09 2018
    ## 1694  Camion Grande  09 2018
    ## 1695  Camion Grande  09 2018
    ## 1696  Camion Grande  09 2018
    ## 1697  Camion Grande  09 2018
    ## 1698          Panel  09 2018
    ## 1699          Panel  09 2018
    ## 1700  Camion Grande  09 2018
    ## 1701 Camion Pequeño  09 2018
    ## 1702  Camion Grande  09 2018
    ## 1703          Panel  09 2018
    ## 1704 Camion Pequeño  09 2018
    ## 1705 Camion Pequeño  09 2018
    ## 1706 Camion Pequeño  09 2018
    ## 1707  Camion Grande  09 2018
    ## 1708  Camion Grande  09 2018
    ## 1709 Camion Pequeño  09 2018
    ## 1710  Camion Grande  09 2018
    ## 1711          Panel  09 2018
    ## 1712  Camion Grande  09 2018
    ## 1713 Camion Pequeño  09 2018
    ## 1714 Camion Pequeño  09 2018
    ## 1715  Camion Grande  09 2018
    ## 1716  Camion Grande  09 2018
    ## 1717  Camion Grande  09 2018
    ## 1718  Camion Grande  09 2018
    ## 1719 Camion Pequeño  09 2018
    ## 1720  Camion Grande  09 2018
    ## 1721  Camion Grande  09 2018
    ## 1722  Camion Grande  09 2018
    ## 1723  Camion Grande  09 2018
    ## 1724 Camion Pequeño  09 2018
    ## 1725 Camion Pequeño  09 2018
    ## 1726 Camion Pequeño  09 2018
    ## 1727  Camion Grande  09 2018
    ## 1728 Camion Pequeño  09 2018
    ## 1729  Camion Grande  09 2018
    ## 1730  Camion Grande  09 2018
    ## 1731 Camion Pequeño  09 2018
    ## 1732  Camion Grande  09 2018
    ## 1733  Camion Grande  09 2018
    ## 1734          Panel  09 2018
    ## 1735          Panel  09 2018
    ## 1736  Camion Grande  09 2018
    ## 1737 Camion Pequeño  09 2018
    ## 1738          Panel  09 2018
    ## 1739  Camion Grande  09 2018
    ## 1740  Camion Grande  09 2018
    ## 1741          Panel  09 2018
    ## 1742          Panel  09 2018
    ## 1743  Camion Grande  09 2018
    ## 1744  Camion Grande  09 2018
    ## 1745          Panel  09 2018
    ## 1746  Camion Grande  09 2018
    ## 1747 Camion Pequeño  09 2018
    ## 1748  Camion Grande  09 2018
    ## 1749 Camion Pequeño  09 2018
    ## 1750 Camion Pequeño  09 2018
    ## 1751          Panel  09 2018
    ## 1752  Camion Grande  09 2018
    ## 1753 Camion Pequeño  09 2018
    ## 1754          Panel  09 2018
    ## 1755  Camion Grande  09 2018
    ## 1756 Camion Pequeño  09 2018
    ## 1757  Camion Grande  09 2018
    ## 1758 Camion Pequeño  09 2018
    ## 1759 Camion Pequeño  09 2018
    ## 1760  Camion Grande  09 2018
    ## 1761  Camion Grande  09 2018
    ## 1762          Panel  09 2018
    ## 1763  Camion Grande  09 2018
    ## 1764  Camion Grande  09 2018
    ## 1765  Camion Grande  09 2018
    ## 1766  Camion Grande  09 2018
    ## 1767  Camion Grande  09 2018
    ## 1768 Camion Pequeño  09 2018
    ## 1769          Panel  09 2018
    ## 1770  Camion Grande  09 2018
    ## 1771  Camion Grande  09 2018
    ## 1772  Camion Grande  09 2018
    ## 1773  Camion Grande  09 2018
    ## 1774  Camion Grande  09 2018
    ## 1775  Camion Grande  09 2018
    ## 1776  Camion Grande  09 2018
    ## 1777  Camion Grande  09 2018
    ## 1778          Panel  09 2018
    ## 1779  Camion Grande  09 2018
    ## 1780 Camion Pequeño  09 2018
    ## 1781 Camion Pequeño  09 2018
    ## 1782 Camion Pequeño  09 2018
    ## 1783 Camion Pequeño  09 2018
    ## 1784 Camion Pequeño  10 2018
    ## 1785          Panel  10 2018
    ## 1786  Camion Grande  10 2018
    ## 1787          Panel  10 2018
    ## 1788  Camion Grande  10 2018
    ## 1789  Camion Grande  10 2018
    ## 1790  Camion Grande  10 2018
    ## 1791  Camion Grande  10 2018
    ## 1792 Camion Pequeño  10 2018
    ## 1793 Camion Pequeño  10 2018
    ## 1794  Camion Grande  10 2018
    ## 1795          Panel  10 2018
    ## 1796  Camion Grande  10 2018
    ## 1797  Camion Grande  10 2018
    ## 1798          Panel  10 2018
    ## 1799  Camion Grande  10 2018
    ## 1800  Camion Grande  10 2018
    ## 1801  Camion Grande  10 2018
    ## 1802  Camion Grande  10 2018
    ## 1803 Camion Pequeño  10 2018
    ## 1804  Camion Grande  10 2018
    ## 1805 Camion Pequeño  10 2018
    ## 1806  Camion Grande  10 2018
    ## 1807          Panel  10 2018
    ## 1808  Camion Grande  10 2018
    ## 1809  Camion Grande  10 2018
    ## 1810 Camion Pequeño  10 2018
    ## 1811  Camion Grande  10 2018
    ## 1812  Camion Grande  10 2018
    ## 1813  Camion Grande  10 2018
    ## 1814  Camion Grande  10 2018
    ## 1815  Camion Grande  10 2018
    ## 1816 Camion Pequeño  10 2018
    ## 1817  Camion Grande  10 2018
    ## 1818 Camion Pequeño  10 2018
    ## 1819          Panel  10 2018
    ## 1820  Camion Grande  10 2018
    ## 1821  Camion Grande  10 2018
    ## 1822  Camion Grande  10 2018
    ## 1823 Camion Pequeño  10 2018
    ## 1824 Camion Pequeño  10 2018
    ## 1825  Camion Grande  10 2018
    ## 1826  Camion Grande  10 2018
    ## 1827          Panel  10 2018
    ## 1828  Camion Grande  10 2018
    ## 1829  Camion Grande  10 2018
    ## 1830  Camion Grande  10 2018
    ## 1831  Camion Grande  10 2018
    ## 1832 Camion Pequeño  10 2018
    ## 1833  Camion Grande  10 2018
    ## 1834 Camion Pequeño  10 2018
    ## 1835  Camion Grande  10 2018
    ## 1836 Camion Pequeño  10 2018
    ## 1837  Camion Grande  10 2018
    ## 1838  Camion Grande  10 2018
    ## 1839          Panel  10 2018
    ## 1840          Panel  10 2018
    ## 1841  Camion Grande  10 2018
    ## 1842  Camion Grande  10 2018
    ## 1843 Camion Pequeño  10 2018
    ## 1844  Camion Grande  10 2018
    ## 1845  Camion Grande  10 2018
    ## 1846 Camion Pequeño  10 2018
    ## 1847  Camion Grande  10 2018
    ## 1848 Camion Pequeño  10 2018
    ## 1849 Camion Pequeño  10 2018
    ## 1850          Panel  10 2018
    ## 1851  Camion Grande  10 2018
    ## 1852  Camion Grande  10 2018
    ## 1853  Camion Grande  10 2018
    ## 1854          Panel  10 2018
    ## 1855  Camion Grande  10 2018
    ## 1856  Camion Grande  10 2018
    ## 1857 Camion Pequeño  10 2018
    ## 1858          Panel  10 2018
    ## 1859  Camion Grande  10 2018
    ## 1860 Camion Pequeño  10 2018
    ## 1861  Camion Grande  10 2018
    ## 1862 Camion Pequeño  10 2018
    ## 1863  Camion Grande  10 2018
    ## 1864  Camion Grande  10 2018
    ## 1865  Camion Grande  10 2018
    ## 1866  Camion Grande  10 2018
    ## 1867  Camion Grande  10 2018
    ## 1868          Panel  10 2018
    ## 1869 Camion Pequeño  10 2018
    ## 1870 Camion Pequeño  10 2018
    ## 1871 Camion Pequeño  10 2018
    ## 1872          Panel  10 2018
    ## 1873 Camion Pequeño  10 2018
    ## 1874          Panel  10 2018
    ## 1875  Camion Grande  10 2018
    ## 1876 Camion Pequeño  10 2018
    ## 1877  Camion Grande  10 2018
    ## 1878 Camion Pequeño  10 2018
    ## 1879 Camion Pequeño  10 2018
    ## 1880          Panel  10 2018
    ## 1881 Camion Pequeño  10 2018
    ## 1882  Camion Grande  10 2018
    ## 1883  Camion Grande  10 2018
    ## 1884 Camion Pequeño  10 2018
    ## 1885 Camion Pequeño  10 2018
    ## 1886  Camion Grande  10 2018
    ## 1887 Camion Pequeño  10 2018
    ## 1888 Camion Pequeño  10 2018
    ## 1889 Camion Pequeño  10 2018
    ## 1890 Camion Pequeño  10 2018
    ## 1891  Camion Grande  10 2018
    ## 1892 Camion Pequeño  10 2018
    ## 1893  Camion Grande  10 2018
    ## 1894 Camion Pequeño  10 2018
    ## 1895  Camion Grande  10 2018
    ## 1896  Camion Grande  10 2018
    ## 1897  Camion Grande  10 2018
    ## 1898  Camion Grande  10 2018
    ## 1899          Panel  10 2018
    ## 1900  Camion Grande  10 2018
    ## 1901 Camion Pequeño  10 2018
    ## 1902          Panel  10 2018
    ## 1903 Camion Pequeño  10 2018
    ## 1904  Camion Grande  10 2018
    ## 1905  Camion Grande  10 2018
    ## 1906  Camion Grande  10 2018
    ## 1907  Camion Grande  10 2018
    ## 1908  Camion Grande  10 2018
    ## 1909 Camion Pequeño  10 2018
    ## 1910 Camion Pequeño  10 2018
    ## 1911 Camion Pequeño  10 2018
    ## 1912 Camion Pequeño  10 2018
    ## 1913  Camion Grande  10 2018
    ## 1914 Camion Pequeño  10 2018
    ## 1915  Camion Grande  10 2018
    ## 1916  Camion Grande  10 2018
    ## 1917  Camion Grande  10 2018
    ## 1918 Camion Pequeño  10 2018
    ## 1919 Camion Pequeño  10 2018
    ## 1920          Panel  10 2018
    ## 1921  Camion Grande  10 2018
    ## 1922  Camion Grande  10 2018
    ## 1923  Camion Grande  10 2018
    ## 1924 Camion Pequeño  10 2018
    ## 1925 Camion Pequeño  10 2018
    ## 1926          Panel  10 2018
    ## 1927  Camion Grande  10 2018
    ## 1928 Camion Pequeño  10 2018
    ## 1929 Camion Pequeño  10 2018
    ## 1930 Camion Pequeño  10 2018
    ## 1931  Camion Grande  10 2018
    ## 1932 Camion Pequeño  10 2018
    ## 1933 Camion Pequeño  10 2018
    ## 1934  Camion Grande  10 2018
    ## 1935          Panel  10 2018
    ## 1936          Panel  10 2018
    ## 1937          Panel  10 2018
    ## 1938  Camion Grande  10 2018
    ## 1939  Camion Grande  10 2018
    ## 1940  Camion Grande  10 2018
    ## 1941  Camion Grande  10 2018
    ## 1942  Camion Grande  10 2018
    ## 1943  Camion Grande  10 2018
    ## 1944 Camion Pequeño  10 2018
    ## 1945          Panel  10 2018
    ## 1946          Panel  10 2018
    ## 1947  Camion Grande  10 2018
    ## 1948  Camion Grande  10 2018
    ## 1949  Camion Grande  10 2018
    ## 1950 Camion Pequeño  10 2018
    ## 1951  Camion Grande  10 2018
    ## 1952 Camion Pequeño  10 2018
    ## 1953 Camion Pequeño  10 2018
    ## 1954          Panel  10 2018
    ## 1955  Camion Grande  10 2018
    ## 1956 Camion Pequeño  10 2018
    ## 1957  Camion Grande  10 2018
    ## 1958  Camion Grande  10 2018
    ## 1959 Camion Pequeño  10 2018
    ## 1960  Camion Grande  10 2018
    ## 1961 Camion Pequeño  10 2018
    ## 1962  Camion Grande  10 2018
    ## 1963  Camion Grande  10 2018
    ## 1964  Camion Grande  10 2018
    ## 1965 Camion Pequeño  10 2018
    ## 1966          Panel  10 2018
    ## 1967 Camion Pequeño  10 2018
    ## 1968  Camion Grande  10 2018
    ## 1969  Camion Grande  10 2018
    ## 1970  Camion Grande  10 2018
    ## 1971  Camion Grande  10 2018
    ## 1972  Camion Grande  10 2018
    ## 1973  Camion Grande  10 2018
    ## 1974  Camion Grande  10 2018
    ## 1975  Camion Grande  10 2018
    ## 1976  Camion Grande  10 2018
    ## 1977  Camion Grande  10 2018
    ## 1978 Camion Pequeño  10 2018
    ## 1979  Camion Grande  10 2018
    ## 1980  Camion Grande  10 2018
    ## 1981          Panel  10 2018
    ## 1982          Panel  10 2018
    ## 1983 Camion Pequeño  10 2018
    ## 1984  Camion Grande  11 2018
    ## 1985  Camion Grande  11 2018
    ## 1986 Camion Pequeño  11 2018
    ## 1987 Camion Pequeño  11 2018
    ## 1988  Camion Grande  11 2018
    ## 1989 Camion Pequeño  11 2018
    ## 1990  Camion Grande  11 2018
    ## 1991 Camion Pequeño  11 2018
    ## 1992  Camion Grande  11 2018
    ## 1993  Camion Grande  11 2018
    ## 1994  Camion Grande  11 2018
    ## 1995  Camion Grande  11 2018
    ## 1996  Camion Grande  11 2018
    ## 1997  Camion Grande  11 2018
    ## 1998 Camion Pequeño  11 2018
    ## 1999          Panel  11 2018
    ## 2000  Camion Grande  11 2018
    ## 2001  Camion Grande  11 2018
    ## 2002  Camion Grande  11 2018
    ## 2003  Camion Grande  11 2018
    ## 2004  Camion Grande  11 2018
    ## 2005  Camion Grande  11 2018
    ## 2006  Camion Grande  11 2018
    ## 2007          Panel  11 2018
    ## 2008 Camion Pequeño  11 2018
    ## 2009 Camion Pequeño  11 2018
    ## 2010  Camion Grande  11 2018
    ## 2011  Camion Grande  11 2018
    ## 2012  Camion Grande  11 2018
    ## 2013          Panel  11 2018
    ## 2014  Camion Grande  11 2018
    ## 2015  Camion Grande  11 2018
    ## 2016          Panel  11 2018
    ## 2017  Camion Grande  11 2018
    ## 2018 Camion Pequeño  11 2018
    ## 2019  Camion Grande  11 2018
    ## 2020 Camion Pequeño  11 2018
    ## 2021  Camion Grande  11 2018
    ## 2022  Camion Grande  11 2018
    ## 2023 Camion Pequeño  11 2018
    ## 2024  Camion Grande  11 2018
    ## 2025 Camion Pequeño  11 2018
    ## 2026  Camion Grande  11 2018
    ## 2027  Camion Grande  11 2018
    ## 2028  Camion Grande  11 2018
    ## 2029 Camion Pequeño  11 2018
    ## 2030  Camion Grande  11 2018
    ## 2031 Camion Pequeño  11 2018
    ## 2032 Camion Pequeño  11 2018
    ## 2033  Camion Grande  11 2018
    ## 2034 Camion Pequeño  11 2018
    ## 2035  Camion Grande  11 2018
    ## 2036 Camion Pequeño  11 2018
    ## 2037          Panel  11 2018
    ## 2038          Panel  11 2018
    ## 2039 Camion Pequeño  11 2018
    ## 2040  Camion Grande  11 2018
    ## 2041 Camion Pequeño  11 2018
    ## 2042  Camion Grande  11 2018
    ## 2043  Camion Grande  11 2018
    ## 2044 Camion Pequeño  11 2018
    ## 2045 Camion Pequeño  11 2018
    ## 2046  Camion Grande  11 2018
    ## 2047  Camion Grande  11 2018
    ## 2048  Camion Grande  11 2018
    ## 2049  Camion Grande  11 2018
    ## 2050  Camion Grande  11 2018
    ## 2051 Camion Pequeño  11 2018
    ## 2052  Camion Grande  11 2018
    ## 2053 Camion Pequeño  11 2018
    ## 2054  Camion Grande  11 2018
    ## 2055  Camion Grande  11 2018
    ## 2056  Camion Grande  11 2018
    ## 2057          Panel  11 2018
    ## 2058  Camion Grande  11 2018
    ## 2059          Panel  11 2018
    ## 2060  Camion Grande  11 2018
    ## 2061  Camion Grande  11 2018
    ## 2062  Camion Grande  11 2018
    ## 2063  Camion Grande  11 2018
    ## 2064  Camion Grande  11 2018
    ## 2065 Camion Pequeño  11 2018
    ## 2066  Camion Grande  11 2018
    ## 2067  Camion Grande  11 2018
    ## 2068          Panel  11 2018
    ## 2069          Panel  11 2018
    ## 2070  Camion Grande  11 2018
    ## 2071  Camion Grande  11 2018
    ## 2072 Camion Pequeño  11 2018
    ## 2073 Camion Pequeño  11 2018
    ## 2074          Panel  11 2018
    ## 2075 Camion Pequeño  11 2018
    ## 2076          Panel  11 2018
    ## 2077  Camion Grande  11 2018
    ## 2078 Camion Pequeño  11 2018
    ## 2079 Camion Pequeño  11 2018
    ## 2080  Camion Grande  11 2018
    ## 2081  Camion Grande  11 2018
    ## 2082          Panel  11 2018
    ## 2083 Camion Pequeño  11 2018
    ## 2084  Camion Grande  11 2018
    ## 2085  Camion Grande  11 2018
    ## 2086  Camion Grande  11 2018
    ## 2087  Camion Grande  11 2018
    ## 2088          Panel  11 2018
    ## 2089          Panel  11 2018
    ## 2090  Camion Grande  11 2018
    ## 2091  Camion Grande  11 2018
    ## 2092 Camion Pequeño  11 2018
    ## 2093  Camion Grande  11 2018
    ## 2094 Camion Pequeño  11 2018
    ## 2095 Camion Pequeño  11 2018
    ## 2096 Camion Pequeño  11 2018
    ## 2097  Camion Grande  11 2018
    ## 2098  Camion Grande  11 2018
    ## 2099  Camion Grande  11 2018
    ## 2100 Camion Pequeño  11 2018
    ## 2101  Camion Grande  11 2018
    ## 2102 Camion Pequeño  11 2018
    ## 2103  Camion Grande  11 2018
    ## 2104 Camion Pequeño  11 2018
    ## 2105  Camion Grande  11 2018
    ## 2106  Camion Grande  11 2018
    ## 2107 Camion Pequeño  11 2018
    ## 2108          Panel  11 2018
    ## 2109 Camion Pequeño  11 2018
    ## 2110  Camion Grande  11 2018
    ## 2111  Camion Grande  11 2018
    ## 2112  Camion Grande  11 2018
    ## 2113 Camion Pequeño  11 2018
    ## 2114          Panel  11 2018
    ## 2115  Camion Grande  11 2018
    ## 2116  Camion Grande  11 2018
    ## 2117  Camion Grande  11 2018
    ## 2118  Camion Grande  11 2018
    ## 2119  Camion Grande  11 2018
    ## 2120 Camion Pequeño  11 2018
    ## 2121  Camion Grande  11 2018
    ## 2122  Camion Grande  11 2018
    ## 2123  Camion Grande  11 2018
    ## 2124  Camion Grande  11 2018
    ## 2125  Camion Grande  11 2018
    ## 2126  Camion Grande  11 2018
    ## 2127  Camion Grande  11 2018
    ## 2128          Panel  11 2018
    ## 2129          Panel  11 2018
    ## 2130  Camion Grande  11 2018
    ## 2131 Camion Pequeño  11 2018
    ## 2132 Camion Pequeño  11 2018
    ## 2133  Camion Grande  11 2018
    ## 2134  Camion Grande  11 2018
    ## 2135  Camion Grande  11 2018
    ## 2136  Camion Grande  11 2018
    ## 2137  Camion Grande  11 2018
    ## 2138  Camion Grande  11 2018
    ## 2139 Camion Pequeño  11 2018
    ## 2140  Camion Grande  11 2018
    ## 2141  Camion Grande  11 2018
    ## 2142  Camion Grande  11 2018
    ## 2143 Camion Pequeño  11 2018
    ## 2144          Panel  11 2018
    ## 2145          Panel  11 2018
    ## 2146  Camion Grande  11 2018
    ## 2147  Camion Grande  11 2018
    ## 2148 Camion Pequeño  11 2018
    ## 2149  Camion Grande  11 2018
    ## 2150  Camion Grande  11 2018
    ## 2151  Camion Grande  11 2018
    ## 2152  Camion Grande  11 2018
    ## 2153          Panel  11 2018
    ## 2154  Camion Grande  11 2018
    ## 2155  Camion Grande  11 2018
    ## 2156  Camion Grande  11 2018
    ## 2157  Camion Grande  11 2018
    ## 2158 Camion Pequeño  11 2018
    ## 2159 Camion Pequeño  11 2018
    ## 2160  Camion Grande  11 2018
    ## 2161  Camion Grande  11 2018
    ## 2162  Camion Grande  11 2018
    ## 2163 Camion Pequeño  11 2018
    ## 2164  Camion Grande  11 2018
    ## 2165          Panel  11 2018
    ## 2166 Camion Pequeño  11 2018
    ## 2167  Camion Grande  11 2018
    ## 2168          Panel  11 2018
    ## 2169  Camion Grande  11 2018
    ## 2170  Camion Grande  11 2018
    ## 2171 Camion Pequeño  11 2018
    ## 2172  Camion Grande  11 2018
    ## 2173  Camion Grande  11 2018
    ## 2174  Camion Grande  11 2018
    ## 2175 Camion Pequeño  11 2018
    ## 2176 Camion Pequeño  11 2018
    ## 2177 Camion Pequeño  11 2018
    ## 2178  Camion Grande  11 2018
    ## 2179 Camion Pequeño  11 2018
    ## 2180  Camion Grande  11 2018

``` r
write.csv(df1, file = 'datosembotelladora.csv')
```

``` r
a <- c(1,2,2,3,3,3,4,4,5,5)
b <- c(2,2,2,2,3,3,3,3,4)
c <- c(3,3,3,3,3,4,4,4,4)
lista_vectores <- list(a,b,c)
moda <- lapply(lista_vectores,function(i){
  ux <- unique(i)
  ux[which.max(tabulate(match(i, ux)))]
})
moda
```

    ## [[1]]
    ## [1] 3
    ## 
    ## [[2]]
    ## [1] 2
    ## 
    ## [[3]]
    ## [1] 3

``` r
#file <- "C:/Users/Mafer/Desktop/GitHub/DataWranglingR/Laboratorio 1/INE_PARQUE_VEHICULAR_080219.txt"
#file
#library(readr)
#parque_vehicular <- read.delim(file, header = TRUE, sep = "|", quote = "", dec = ".")
#parque_vehicular
```
