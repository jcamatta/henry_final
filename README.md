# PROYECTO DE GOOGLE & YELP REVIEWS

## Índice
- [Descripción del Repositorio](#descripción-del-repositorio)
- [Contexto](#contexto)
- [Producto Desarrollado](#producto-desarrollado)
  - [Sistema de Recomendación](#sistema-de-recomendación)
  - [NLP Modelos](#nlp-modelos)
- [Stack Tecnológico Empleado](#stack-tecnológico-empleado)
- [Referencias](#referencias)
  - [Documentación](#documentación)
  - [Proyectos Previos Similares](#proyectos-previos-similares)
- [Agradecimientos](#agradecimientos)
<hr>

## Descripción del Repositorio

Esta carpeta construye dos productos: un sistema de recomendacion, y modelos pre-entrenados y fine-tunned por mi mismo de NLP para el analisis de reseñas. 
Se construye finalmente una web interactiva que en conexion con una API permite el uso de ambos productos.

El archivo main.py es la API escrita con el framework FastAPI corazon del proyecto.

El archivo web.py es la Web interactiva construida a partir del framework Streamlit.

La carpeta extra_notebooks contiene todo los codigos notebooks realizados que incluyen, a saber:
- Codigo "pre-cloud" que incluye todo el codigo realizado para convertir JSON files a CSV, transformaciones y carga hacia Google Cloud Storage.
- ETL realizado al dataset de Google y Yelp dividos por carpetas, documentados y enumerados.
- En la carpeta nlp_models_notebook, encontraran el preprocessing y fine-tunning notebooks asociado a cada modelo realizado.
- La carpeta modelos incluye el codigo para el uso del sistema de recomendacion y de los modelos NLP.
- La carpeta .streamlit contiene el tema que se utilizo para crear el pagina web de streamlit.
- Por ultimo, la carpeta presentaciones contiene las diapositivas usadas en la presentacion del proyecto. Van de la semana 1 hasta la semana 4. La semana 2 no esta, puesto que no me correspondia presentar nada en la misma.

Lamentablemente, el proyecto no se pudo deployar permanentemente puesto que el dataset con el que hace uso el sistema de recomendacion, a si como los modelos de NLP, pesan en conjunto por arriba de los 25GB. Sin embargo, se realizo un video del streamlit para pudiesen observar su funcionalidad. 

LINK del video al prototipo finalizado: https://youtu.be/06DGSMYYzx4

<hr>

## Contexto

Dado que la opinion de los usuarios es muy relevante hoy dia, y puede servir a la mejor toma de decisiones. En este proyecto se nos
brindo de dos datasets de millones de reviews que correspondian a las plataformas de Google y Yelp localizado en Estados Unidos. Yelp es una plataforma de reseñas para empresas de todo
tipo, como hoteles, restaurantes, etc. Mientras que Google cuanta con su propia plataforma de reviews. En forma resumida, el dataset contenia dos tipos de archivos:
- Metadata: informacion referida a las empresas
- Reviews: una tabla de hecho que corresponde a las reviews realizadas por los usuarios.

A groso modo, el tamaño de para cada plataforma eran:
- Google: 2M de empresas y 43M de reviews distribuidas en los 51 estados de Estados Unidos.
- Yelp: 115Mil empresas y 6M de reviews.

A partir de ello, al equipo de Machine Learning se le pidio realizar como MVP un sistema de recomendacion.
<hr>

## Producto Desarrollado


### Sistema de Recomendación

El sistema de recomendacion es un sistema hibrido. El usuario ingresa 4 inputs, a saber:
1. Su id de usuario.
2. Su geolocalizacion
3. La categoria de empresas de las que quiere recibir recomendaciones.
4. La distancia de dichas empresas a el.
Dada estas empresas, se le realiza un **FILTRO COLABORATIVO** **USER BASED**. Se obtiene una prediccion del rating dado por el usuario a las empresas que no visito.
Se filtran aquellas empresas que el modelo predice que el usuario mejor rankearia (un rating mayor a 4).

Por ultimo, a las empresas mejor rankeadas se busca aquella mas similar a las que el usuario previamente ha visitado. Se filtran aquellas con mayor valor de similitud.
Estas ultimas son las recomendadas por el modelo.


### NLP Modelos

Esta area incluye varios modelos, algunos pre-entrenados y otros fine-tunneados a partir de un modelo base. Las tareas que realizan los modelos son:
1. Prediccion del rating de la review.
2. Clasificacion de la review entre useful, cool, o funny.
3. Respuestas automaticas a reviews basandose en el contexto.
4. Resumen de reviews.
<hr>

## Stack Tecnológico Empleado

Dado que los datasets eran muy pesados (mas de 5GBs) requerimos el uso de tecnicas mas sofisticadas que las tradicionales como pandas. Por ello, usamos:
- Datasets de HuggingFace
- Polars
Para crear el sistema de recomendacion:
- Surprise
- Scikit-Learn
Para entrenar y hacer uso de los modelos NLP:
- Transformers
- Tensorflow
Para la creacion de la API y la pagina WEB:
- FastAPI
- Streamlit
Para los graficos geo-espaciales en Streamlit:
- Folium
- Streamlit-Folium
Otras:
- Requests
- Spacy
- Numpy
- Sqlite3
- SqlAlchemy
<hr>

## Referencias

A continuacion paso recomendar las paginas webs y documentaciones con las que me base para realizar este proyecto.


### Documentación

https://huggingface.co/docs/transformers/index

https://huggingface.co/docs/datasets/index

https://huggingface.co/learn/nlp-course/chapter1/1

https://pola-rs.github.io/polars/py-polars/html/reference/

https://docs.streamlit.io/

https://github.com/randyzwitch/streamlit-folium

https://surprise.readthedocs.io/en/stable/

https://fastapi.tiangolo.com/


### Proyectos Previos Similares

En este uso streamlit.

https://github.com/jcamatta/henry_labs_02

En este creo un sistema de recomendacion.

https://github.com/jcamatta/henry_labs_02
<hr>

## Agradecimientos

Muchas gracias a todos por leer esta extensa documentacion. 

Gracias a mis compañeros con los que hubiese sido imposible realizar este proyecto.

Gracias al mentor por dar buenos tips y ayudar con el desarrollo del proyecto.

Gracias a mi por no rendirme y seguir esforzandome.