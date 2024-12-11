# Clasificación de Textos con TF-IDF

Este proyecto tiene como objetivo clasificar automáticamente textos en tres categorías diferentes: **deportivos**, **políticos** y **de entretenimiento**. Para ello, se utiliza la técnica de codificación **TF-IDF** (Term Frequency-Inverse Document Frequency) y dos métodos de similitud: **similitud del coseno** y **similitud euclidiana**.

## Descripción del Problema

La tarea consiste en entrenar un modelo para determinar a qué categoría pertenece un nuevo texto de consulta. El corpus de entrenamiento contiene textos clasificados en las tres categorías mencionadas, y el objetivo es predecir la categoría de un nuevo texto.

Para este propósito, se lleva a cabo lo siguiente:

1. **Preprocesamiento de los textos**: Carga, limpieza y eliminación de stop words.
2. **Codificación TF-IDF**: Conversión de los textos en vectores numéricos.
3. **Similitud del Coseno y Euclidiana**: Cálculo de la similitud entre el texto de consulta y los documentos del corpus.
4. **Clasificación**: Determinación de la categoría más probable para un nuevo texto de consulta.

## Objetivos

El proyecto busca desarrollar un sistema que sea capaz de:

1. Preprocesar textos para eliminar ruido y normalizar el contenido.
2. Codificar textos utilizando TF-IDF para representar la importancia de las palabras.
3. Implementar la similitud de coseno para comparar documentos y clasificarlos.
4. Desarrollar una función de clasificación que reciba un texto y devuelva la categoría más probable.

---
## Métodos Utilizados

### 1. **Similitud del Coseno**

La similitud del coseno mide la similitud entre dos vectores en un espacio multidimensional. El cálculo se basa en la relación angular entre los vectores representados por los documentos.

**Fórmula de la similitud del coseno**:
$$
\text{similitud\_coseno} = \frac{A \cdot B}{\|A\| \|B\|}
$$

**Implementación**:
1. Se calculan los vectores TF-IDF para la consulta y el corpus.
2. Se calcula el producto punto entre los vectores y las normas (longitudes) de los mismos.
3. Se devuelve la similitud coseno.

### 2. **Similitud Euclidiana**

La similitud euclidiana mide la distancia entre dos puntos en un espacio n-dimensional. A menor distancia, mayor similitud.

**Fórmula de la distancia euclidiana**:
$$
\text{distancia\_euclidiana} = \sqrt{\sum_{i} (x_i - y_i)^2}
$$

**Implementación**:
1. Se calcula la diferencia al cuadrado entre las características de los vectores.
2. Se suma la diferencia para cada dimensión y se calcula la raíz cuadrada.

---

## Librerías utilizadas

Este proyecto utiliza las siguientes librerías y módulos estándar de Python:

- **math**: Se utiliza para realizar cálculos matemáticos, como el cálculo de la raíz cuadrada y otras operaciones necesarias para las fórmulas de similitud.
- **glob**: Se utiliza para manejar patrones de búsqueda de archivos y obtener los archivos del corpus de entrenamiento.
- **os**: Se utiliza para interactuar con el sistema operativo, como la carga de archivos y la gestión de directorios.

No se requieren dependencias externas para ejecutar este proyecto, ya que todas las librerías utilizadas son parte de la biblioteca estándar de Python.

---
## Resultados

### Modelos Evaluados

| **Modelo** | **Función de Similitud** | **Accuracy** (Tasa de acierto) |
|---|---|---|
| 01 | Coseno | 100% |
| 02 | Euclídea | 75% |

### Explicación de los Resultados

- **Similitud del Coseno**: La similitud del coseno muestra un rendimiento del 100% en la clasificación. Esto indica que la representación de los documentos como vectores TF-IDF, junto con el cálculo de la similitud del coseno, es altamente efectiva para este conjunto de datos.
  
- **Similitud Euclidiana**: La similitud euclidiana tiene un rendimiento inferior al de la similitud del coseno (75%). Esto podría deberse a que la similitud euclidiana no captura adecuadamente las relaciones semánticas entre las palabras, como lo hace el coseno.

## Implementación

El código del proyecto se organiza en las siguientes funciones principales:

- **`preprocesamiento(texto)`**: Limpieza del texto, eliminación de stop words y tokenización.
- **`tf_idf(corpus)`**: Función para calcular el peso de los términos en los documentos usando la técnica TF-IDF.
- **`coseno(query_codificado, corpus_codificado)`**: Cálculo de la similitud del coseno entre el texto de consulta y los documentos del corpus.
- **`euclides(query_codificado, corpus_codificado)`**: Cálculo de la similitud euclidiana entre el texto de consulta y los documentos del corpus.
- **`pertenece_a(corpus, query_texto)`**: Función de clasificación que toma un texto de consulta como entrada y devuelve la categoría más probable.

---
## Consideraciones sobre el Diccionario y el Dataset

La eficacia del algoritmo de clasificación depende en gran medida del **diccionario** utilizado, es decir, de las palabras clave que se seleccionan para construir los vectores TF-IDF. El **diccionario** es crucial porque las palabras que contiene afectan directamente a los vectores y, por lo tanto, a las mediciones de similitud entre los documentos. Un diccionario bien construido y representativo de los temas de los textos permitirá obtener mejores resultados en la clasificación.

Además, el rendimiento del modelo puede variar dependiendo del **dataset** utilizado. En este proyecto, se usó un conjunto de datos específico con textos clasificados en tres categorías: deportivos, políticos y de entretenimiento. Sin embargo, el código puede ser adaptado para trabajar con otros datasets que contengan diferentes categorías o textos. 

Es importante tener en cuenta que, al cambiar el dataset, el modelo puede necesitar ser ajustado, y los resultados pueden variar dependiendo de la calidad y relevancia del nuevo conjunto de datos. Si se decide utilizar un nuevo dataset, es recomendable realizar un análisis preliminar sobre su estructura y el preprocesamiento necesario antes de aplicar el modelo.

### Cómo cambiar el Dataset

1. Asegúrate de que el nuevo dataset tenga una estructura similar al utilizado en el proyecto. Es decir, que contenga documentos clasificados en diferentes categorías.
2. Realiza el preprocesamiento necesario (eliminación de stop words, tokenización, etc.) antes de pasar los textos al modelo.
3. Ajusta el código si es necesario para que se adapte a las características del nuevo dataset.

---

## Licencia

Este proyecto está bajo la **Licencia MIT**. Esto significa que puedes usar, copiar, modificar y distribuir el código de este repositorio de forma gratuita, siempre que se incluya el aviso de derechos de autor y la declaración de la licencia en todas las copias o partes sustanciales del código.
