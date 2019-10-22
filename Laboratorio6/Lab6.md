Lab6
================
Mafer Pérez
15 de septiembre de 2019

``` r
library(stringr)
# 1. Placas de vehículo partícular
#answer1 <- c(TRUE, TRUE, TRUE, FALSE, FALSE, FALSE)
str_detect(
  string = c("P243CNJ", "P214HNS", "P345FVJ", "A344SDF", "P2314ASD", "P245ABC"), 
  pattern = "^P[0-9]{3}[BCDFGHJKLMNPQRSTVWXY]{3}$"
)
```

    ## [1]  TRUE  TRUE  TRUE FALSE FALSE FALSE

``` r
#2. Archivo es de tipo pdf o jpg
#answer2 <- c(TRUE, TRUE, TRUE, TRUE, FALSE)
str_detect(
  string = c("Ejemplo1.pdf", "prueba2.PDF", "respuestas_del_examen.jpg", "amor.JPG", "hola.hpq"), 
  pattern = "[[:alnum:]](.PDF|.JPG|.pdf|.jpg)"
  )
```

    ## [1]  TRUE  TRUE  TRUE  TRUE FALSE

``` r
#3. Validar contraseñas de correo Caracter especial, numero y mayúscula
#answer3 <- c(TRUE, TRUE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, TRUE)
str_detect(
  string = c("Hola123!", "$H123488", "$H123488Nu", "AERFSdnf", "12345678", "asdfghjk", "ASDFGHJK", "adfd!!1L", "Datawrangling2019!"), 
  pattern = "[A-Z]{1,}[^[:punct:]]{1,}[0-9]{1,}"
)
```

    ## [1]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE

``` r
#4. Carnet de la universidad desde el 1110 hasta el 8970
#answer4 <- c(TRUE, FALSE, FALSE, TRUE, TRUE)
str_detect(
  string = c("19002324", "31001564", "14011110", "11008921", "2003421"), 
  pattern = "^([0-2]\\d|(30))(0){2}[1-8][1-9]([1-6][0-9]|(70))$"
)
```

    ## [1]  TRUE FALSE FALSE  TRUE FALSE

``` r
#5. Cree una expresión regular que encuentre todas las palabras de la primera linea,
#pero ninguna de la segunda. (2)
#a. pit, spot, spate, slap two, respite
#b. pt,Pot,peat,part
str_detect(
  string = c("pit","spot", "spate", "slap two", "respite", "pt", "Pot", "peat", "part"), 
  pattern = "^(s|sla|res)?p.t[^\\s]?"
)
```

    ## [1]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE

``` r
#6. Cree una expresión regular para obtener los números telefónicos de Guatemala.
#Estos pueden contener al inicio +502 o 502, pueden estar separados por un
##espacio en blanco o un guión o juntos. Notar que los números telefónicos
#pueden empezar únicamente con 4,5,6 o 2. (2)
#a. +50254821151, 4210-7640, 52018150, 2434 6854, 11234569,
#50211234578
str_detect(
  string = c("+50254821151", "4210-7640", "52018150", "2434 6854", "11234569","50211234578"), 
  pattern = "^(\\+)?(502)?(4|5|6|2){1}[0-9]{3}(\\s|\\-|\\S)?[0-9]{4}$"
)
```

    ## [1]  TRUE  TRUE  TRUE  TRUE FALSE FALSE

``` r
#7.Genere una expresión regular que sea capaz de obtener correos de la UFM.
str_detect(
  string = c("meperef@ufm.edu", "acef34@ufm.edu", "acef34@ufm.eduss", "fdff@gmail.com", "fdfgdfg@ufm.com"), 
  pattern = "^[A-z0-9]+@(ufm){1}\\.{1}(edu){1}$"
)
```

    ## [1]  TRUE  TRUE FALSE FALSE FALSE

``` r
#8. El id inicia con 0 a 3 letras minúsculas (puede tener 0 letras minusculas hasta tres)
#b. Luego es seguido por una cadena de digitos que puede ser de 2 a 9 digitos respectivamente.
#c. Inmediatemente despues de la cadena de digitos, se encuentra por lo
#menos tres letras mayusculas.
str_detect(
  string = c("aaaa0323AA", "acd0320AAAA", "ASDC932gfdf", "234CCCD", "sds2cd"), 
  pattern = "^[a-z]{0,3}[0-9]{2,9}[A-Z]{3,}$"
)
```

    ## [1] FALSE  TRUE FALSE  TRUE FALSE