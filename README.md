# Clasificación de Perros y Gatos con MLP

Proyecto de clasificación binaria de imágenes utilizando un Perceptrón Multicapa (MLP).

Un MLP es un tipo de red neuronal artificial compuesta por varias capas de neuronas 
conectadas entre sí: una capa de entrada, una o más capas ocultas y una capa de salida. 
Cada neurona procesa la información recibida y la transforma mediante una función de 
activación, permitiendo que la red aprenda patrones complejos a partir de los datos.

## 1. Descripción del problema de negocio

Muchas plataformas de adopción de mascotas, veterinarias y aplicaciones de fotografía 
reciben grandes volúmenes de imágenes sin etiquetar. Clasificar automáticamente si una 
imagen corresponde a un perro o a un gato permite organizar contenido, filtrar bases de 
datos y automatizar procesos que hoy se hacen manualmente, ahorrando tiempo y reduciendo 
errores humanos.

En este proyecto se aborda este problema mediante un modelo de clasificación binaria de 
imágenes (perro vs. gato), utilizando el dataset Oxford-IIIT Pet, con el fin de evaluar 
la viabilidad de un enfoque simple (MLP) antes de considerar arquitecturas más complejas.

## 2. Objetivos del proyecto

**Objetivo general:**
Desarrollar un modelo de clasificación binaria de imágenes (perro vs. gato) utilizando 
un Perceptrón Multicapa (MLP), evaluando su desempeño y limitaciones frente a este tipo 
de tareas.

**Objetivos específicos:**
- Seleccionar y preparar un subconjunto del dataset Oxford-IIIT Pet para la tarea de 
  clasificación binaria.
- Aplicar preprocesamiento adecuado a las imágenes (normalización, redimensionamiento, 
  aplanado) para su uso en un MLP.
- Diseñar, entrenar y validar una arquitectura MLP para el problema definido.
- Evaluar el desempeño del modelo mediante métricas de clasificación (Accuracy, Precision, 
  Recall, F1-Score, Matriz de Confusión).
- Analizar los errores del modelo e identificar las principales limitaciones de un MLP 
  aplicado a clasificación de imágenes.

## 3. Definición de KPIs

| KPI | Descripción | Meta esperada |
|---|---|---|
| Accuracy | Porcentaje de imágenes correctamente clasificadas sobre el total | ≥ 80% |
| F1-Score | Balance entre precisión y recall, relevante si hay desbalance de clases | ≥ 0.75 |
| Tasa de error por clase | Proporción de errores específicos en "perro" vs. "gato" | Identificar clase con mayor confusión |

## 4. Descripción de las fuentes de datos

El proyecto utiliza el dataset **Oxford-IIIT Pet Dataset**, disponible públicamente en 
Kaggle: https://www.kaggle.com/datasets/tanlikesmath/the-oxfordiiit-pet-dataset

**Características generales del dataset original:**
- 7.349 imágenes en total
- 37 clases (razas distintas de perros y gatos)
- Variabilidad en iluminación, postura y fondo de las imágenes

**Variante definida para este proyecto:**
Para efectos de esta evaluación, se reduce el problema a una **clasificación binaria**: 
perro vs. gato, agrupando todas las razas de perro en una clase y todas las razas de gato 
en otra. Esta decisión se toma para:
- Simplificar el problema y enfocar el análisis en el flujo completo de trabajo (EDA, 
  preprocesamiento, entrenamiento y evaluación) más que en distinguir razas específicas.
- Permitir un entrenamiento más rápido dentro del tiempo asignado (5 horas).
- Facilitar la interpretación de resultados y el análisis de errores, al trabajar con 
  solo 2 clases en lugar de 37.

## 5. Preparación y análisis exploratorio de los datos (EDA)

### 5.1 Carga y organización de los datos
- Cantidad total de imágenes utilizadas: `[completar]`
- Cantidad de imágenes por clase (perro / gato): `[completar]`
- Formato y resolución original de las imágenes: `[completar]`

### 5.2 Calidad de los datos
- Revisión de imágenes corruptas o ilegibles: `[completar]`
- Balance entre clases (¿hay más imágenes de una clase que de otra?): `[completar]`

### 5.3 Visualizaciones
- Ejemplos representativos de cada clase (grilla de imágenes).
- Distribución de tamaños/resoluciones de las imágenes.
- Gráfico de barras con el conteo de imágenes