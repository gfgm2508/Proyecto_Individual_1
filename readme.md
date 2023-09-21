#                       **PROYECTO INDIVIDUAL Nº1**

Este proyecto se desarrolla bajo el rol de MLOps Engineer

# Machine Learning Operations (MLOps)

El proyecto consiste en construir un sistema de recomendación de videojuegos, de la empresa Steam, para usuarios, soportado en datos que han recolectado a lo largo de los años.

Como data scientist se debe realkizar el ciclo comlpeto, es decir, iniciar con en ETL muty detallado sobre la data recibida, continuar con un EDA que permita dar luces sobre la ruta a seguir, construyendo las funciones que la compañia requiere para tomar decisiones y entregar finalmente el modelo de recomendación más ajustado a la realidad de la misma.

## ETL

La data está compuesta por 3 tablas json comprimidas, a saber: steam_games.json.gz, user_reviews.json.gz y users_item.json.gz, las cuales contienen datos anidados, muchos valores nulos y duplicados, campos repetidos entre tablas, entre otras cosas. Dichas tablas están provistas en [PI MLOps - STEAM - Google Drive](https://drive.google.com/drive/folders/1HqBG2-sUkz_R3h1dZU5F2uAzpRn7BSpj).

El proceso de depuración de las tablas se inicia con la conversión de cada archivo jason en un DataFrame de Python, seguido de la desanidación de las columnas de interés, la eliminación de columnas innecesarias para el proceso, la eliminación de registros con valor nulo y duplicados, la corrección del formato de algunos campos, posteriormente, se creó la variable sentiment_analysis en la tabla user_reviews, indispensable para el modelo de recomendación y, por último, se convirtieron a csv las tablas steam_games y user_reviews y a parquet, la tabla users_item, por su gran tamaño.



## Recomendación de juegos

El sistema se basa en una similitud del coseno para calcular la similitud de los juegos mediante los generos y etiquetas.

# API de Recomendación de Juegos en Steam

Esta API proporciona recomendaciones de juegos en la plataforma Steam basadas en el comportamiento de los usuarios y los datos de los juegos disponibles en Steam.

## Cómo Funciona

La API utiliza un algoritmo de filtrado colaborativo basado en el cálculo de similitudes entre juegos. A continuación, se describe el proceso general:

1. **Entrada del Usuario**: El usuario proporciona el ID de un juego como parámetro en la URL al hacer una solicitud GET a `/recomendacion_juego/{product_id}`.

2. **Obtención de Datos del Juego de Referencia**: La API obtiene los datos del juego de referencia con el ID proporcionado por el usuario desde un archivo CSV que contiene información sobre los juegos de Steam.

3. **Procesamiento de Texto**: La API combina las etiquetas (tags) y géneros del juego de referencia en una sola cadena de texto y crea un vectorizador TF-IDF.

4. **Cálculo de Similitud**: La API divide la carga de trabajo en lotes de juegos del archivo CSV y calcula la similitud de coseno entre el juego de referencia y cada juego en el lote utilizando el vectorizador TF-IDF.

5. **Recomendación de Juegos**: La API identifica algún juego similar para recomendar.



## Función userdata

Además de la función principal de recomendación de películas, el proyecto también incluye una función que dado un id de usuario:

- Devuelve la cantidad de dinero gastado.

- El porcentaje de juegos recomendados.

-  La cantidad de items.

  

## Links

- Repositorio (Github): [GitHub - AlejandroManrrique/Proyecto_Individual](https://github.com/AlejandroManrrique/Proyecto_Individual)
- Deploy del Proyecto (Render):[FastAPI - Swagger UI (proyecto-individual-no1-juegos-steam.onrender.com)](https://proyecto-individual-no1-juegos-steam.onrender.com/docs)
- Video (Youtube):https://youtu.be/gCrq1ShNo4k