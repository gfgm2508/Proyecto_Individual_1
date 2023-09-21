#                       **PROYECTO INDIVIDUAL Nº1**

Este proyecto se desarrolla bajo el rol de MLOps Engineer

## Machine Learning Operations (MLOps)

El proyecto consiste en construir un sistema de recomendación de videojuegos, de la empresa Steam, para usuarios, soportado en datos que han recolectado a lo largo de los años.

Como data scientist se debe realizar el ciclo de procesamiento completo, es decir, iniciar con en ETL muty detallado sobre la data recibida, continuar con un EDA que permita dar luces sobre la ruta a seguir, construyendo las funciones que la compañia requiere para tomar decisiones y entregar finalmente el modelo de recomendación más ajustado a la realidad de la misma.

## ETL

La data está compuesta por 3 tablas json comprimidas, a saber: steam_games.json.gz, user_reviews.json.gz y users_item.json.gz, las cuales contienen datos anidados, muchos valores nulos y duplicados, campos repetidos entre tablas, entre otras cosas. Dichas tablas están provistas en [PI MLOps - STEAM - Google Drive](https://drive.google.com/drive/folders/1HqBG2-sUkz_R3h1dZU5F2uAzpRn7BSpj).

El proceso de depuración de las tablas se inicia con la conversión de cada archivo jason en un DataFrame de Python, seguido de la desanidación de las columnas de interés (reviews e items), la eliminación de columnas innecesarias para el proceso, la eliminación de registros con valor nulo y duplicados, la corrección del formato de algunos campos, posteriormente, se creó la variable sentiment_analysis en la tabla user_reviews, indispensable para el modelo de recomendación y, por último, se convirtieron a csv las tablas steam_games y user_reviews y a parquet, la tabla users_item, por su gran tamaño.

## EDA

Se realiza un breve Análisis Exploratorio de Datos para identificar posibles asociaciones entre variables y comportamientos de las mismmas que puedan dar una luz para la construcción del modelo final. Entre los hallazgos, se tiene:

## Desarrollo de API

La propuesta consta de crear 6 funciones: def userdata, def countreviews, def genre, def userforgenre, def developer y def sentiment_analysis. A dichas funciones se crean los respectivos endpoints que consumirá la API, diseñada con el framework FastAPI.

## Modelo de ML

Una vez desarrolada la API, llega el momento para construir el modelo de recomendación más apropiado para los usuarios de Steam. Se han propuesto dos modelos:

- El primero deberá tener una relación ítem-ítem, esto es se toma un item y en base a que tan similar esa ese ítem al resto, se recomiendan similares. Aquí el input es un juego y el output es una lista de juegos recomendados, para ello se recomienda aplicar la similitud del coseno. 
- La otra propuesta para el sistema de recomendación es aplicar el filtro user-item, esto es tomar un usuario, se encuentran usuarios similares y se recomiendan ítems que a esos usuarios similares les gustaron. En este caso el input es un usuario y el output es una lista de juegos que se le recomienda a ese usuario

El líder pide que el modelo derive obligatoriamente en un GET/POST en la API símil al siguiente formato:

Si es un sistema de recomendación itemm-item:
    • def recomendacion_juego: Ingresando el id de producto, deberíamos recibir una lista con 5 juegos recomendados similares al ingresado.

Si es un sistema de recomendación user-item:
    • def recomendacion_usuario( id de usuario ): Ingresando el id de un usuario, deberíamos recibir una lista con 5 juegos recomendados para dicho usuario.

El modeolo a desarrollar es el sistema de recomendación item-item

## Función userdata

Además de la función principal de recomendación de películas, el proyecto también incluye una función que dado un id de usuario:

- Devuelve la cantidad de dinero gastado.

- El porcentaje de juegos recomendados.

-  La cantidad de items.

  

## Links

- Repositorio (Github): [GitHub - Gabriel Gutierrez/Proyecto_Individual_1](https://github.com/gfgm2508/Proyecto_Individual_1)
- Deploy del Proyecto (Render):[FastAPI - Swagger UI (proyecto-individual-no1-juegos-steam.onrender.com)](https://proyecto-individual-no1-juegos-steam.onrender.com/docs)
- Video (Youtube):https://youtu.be/gCrq1ShNo4k

