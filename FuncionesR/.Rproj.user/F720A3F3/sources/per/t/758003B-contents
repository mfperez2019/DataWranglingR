library(readr)
library(tidyverse)
library(tidytext)
text_file <- 'beatles.txt'
readLines(text_file, n=10, encoding = "UTF-8", skipNul = TRUE) #skipnul quita los espacios

#usando readr
beatles_lines <- read_lines(text_file) #Esto hace lo mismo que lo de arriba
beatles_lines

#Para el tiempo que se tarda sirve para cuando son muchos datos
system.time(readLines(text_file, encoding = "UTF-8", skipNul = TRUE))
system.time(read_lines(text_file))

#obtener partes de un string, 10 primeros caracteres de cada linea, del 1 al 10. Es mas rapido porque lo aplica a todo.
substr(beatles_lines, 1,10)

#tokenizar, volver cada palabra de las lineas en un elemento
beatles_frame <- data.frame(txt=beatles_lines)
head(beatles_frame)
beatles_frame$txt <- as.character(beatles_frame$txt)
beatles_words <- unnest_tokens(beatles_frame, input = txt, output = words, token = "words") #cada elemento es una fila
head(beatles_words)

# Contar
beatles_count <- count(beatles_words, words, sort = TRUE)
beatles_count
class(beatles_count)

#limpiar stopwords(articulos o preposiciones que no agregan valor)
library(quanteda)
english_stopwords <- data.frame(words=quanteda::stopwords(language= "en"))
view(english_stopwords)

#antijoin, quita lo que esta en comun de ambos dataframe, que son los stopwords
beatles_words_clean <- anti_join(beatles_words, english_stopwords)
beatles_count <- count(beatles_words_clean, words, sort = TRUE)
beatles_count
