# Analisis #libertadresponsable Uy

Este repositorio contiene los scripts con los que se realizo el analisis de sentimientos de tweets referentes al hashtag #libertadresponsable, en el contexto de la tesis de maestria desarrollada por Macarena Rueco titulada "Alcance del concepto libertad responsable expuesto en canales oficiales digitales durante el gobierno del Presidente Luis Lacalle Pou de Uruguay, en el período comprendido entre marzo 2020 y mayo 2021, desde la perspectiva del Análisis Crítico del Discurso".

# Extracción de tweets

Para la extracción de los tweets se utilizó una herramienta de código abierto desarrollada en el lenguaje de programación Python [Optimized-Modified-GetOldTweets3-OMGOT](https://github.com/marquisvictor/Optimized-Modified-GetOldTweets3-OMGOT) desarrollada por [Victor E. Irekponor](https://github.com/marquisvictor). La misma está basada en un desarrollo también de código abierto: [Get Old Tweets Programatically](https://github.com/Jefferson-Henrique/GetOldTweets-python), desarrollada por [Jefferson Henrique](https://github.com/Jefferson-Henrique).

La instalación se realizó siguiendo las instrucciones del autor tomadas de un [post en medium](https://medium.com/analytics-vidhya/twitter-data-mining-mining-twitter-data-without-api-keys-a2a2bd3f11c) y para la descarga de los tweets se utilizó el siguiente comando que aplica los filtros de fecha y hashtag requeridos:

```bash
# descarga de tweets para el periodo 2020-05-21-2021-05-21
python cli.py --search "#libertadresponsable" --since 2020-05-21 --until 2021-05-21 --csv -o tweets_libertad_responsable.csv

# descarga de tweets para el periodo 2019-05-21-2022-12-17 (historico)
python cli.py --search "#libertadresponsable" --since 2019-05-21 --csv -o tweets_libertad_responsable_historico.csv

```

Los archivos generados se pueden encontrar en el directorio [data/inputs](data/inputs).

# Analisis de sentimiento sobre tweets

Para el análisis de sentimiento de los tweets se utilizó otra herramienta de código abierto: [pysentimiento](https://github.com/pysentimiento/pysentimiento).

Basado en esta herramienta, se utilizó el modelo de inteligencia artificial pre entrenado con tweets en español: [Robertuito](https://github.com/pysentimiento/robertuito/tree/main). Con el mismo se realizaron dos análisis básicos:

- análisis de sentimiento: clasificar tweets positivos, negativos o neutrales
- análisis de emociones: detectar emociones en los tweets (alegría, tristeza, enojo, disgusto, miedo, etc)

Con el resultado de ambos análisis, se clasifican los tweets de la siguiente forma:
- tweets con sentimiento "positivo" -> positivos
- tweets con sentimiento "negativo" -> negativos
- tweets con sentimiento "neutral" y emociones "alegría" -> positivos
- tweets con sentimiento "neutral" y emociones tristeza, enojo, disgusto, miedo -> negativos
- tweets con sentimiento "neutral" y sin determinar emociones -> neutrales

Con estos resultados se generaron planillas para análisis de la información y generación de gráficos.

El codigo utilizado para la ejecución de estos analisis se puede encontrar dentro del directorio [notebooks/](notebooks/).

Por ultimo, los archivos generados con los resultados de los analisis se pueden encontrar en el directorio [data/outputs](data/outputs).
