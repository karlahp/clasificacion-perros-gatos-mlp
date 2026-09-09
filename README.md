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

**Justificación de la elección del dataset:**
Se seleccionó el dataset Oxford-IIIT Pet por sobre las otras alternativas disponibles 
(Intel Image Classification, Los Simpson, PlantVillage) porque plantea un problema de 
clasificación con relevancia práctica directa (identificación de mascotas), cuenta con 
un tamaño de dataset manejable dentro del tiempo disponible para la evaluación, y su 
variabilidad natural en iluminación, postura y fondo lo convierte en un caso de estudio 
realista para evaluar las capacidades y limitaciones de un modelo MLP frente a 
condiciones no controladas.

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
Se trabajó con 7.390 imágenes del dataset Oxford-IIIT Pet, etiquetadas como "perro" o 
"gato" según la convención de nombres del dataset (mayúscula inicial = gato, minúscula = perro).

### 5.2 Calidad de los datos
Se detectó un **desbalance de clases**: 4.990 imágenes de perro (67.5%) y 2.400 de gato 
(32.5%). También se confirmó que las imágenes tienen **tamaños variables** (desde 287x300 
hasta 762x571 píxeles, promedio 437x402 px), por lo que fue necesario redimensionarlas 
a un tamaño uniforme antes del entrenamiento.

### 5.3 Visualizaciones
Se generaron gráficos de distribución de clases y grillas de ejemplos representativos de 
cada clase (ver `images/distribucion_clases.png` y `images/ejemplos_por_clase.png`).

### 5.4 Observaciones y dificultades
La alta variabilidad de iluminación, postura y fondo entre imágenes, sumada al desbalance 
de clases, representan las principales dificultades detectadas para este problema de 
clasificación.

## 6. Metodología utilizada (CRISP-DM)

Este proyecto sigue las etapas de la metodología CRISP-DM:

1. **Comprensión del negocio**: definición del problema de clasificación perro/gato y su utilidad práctica.
2. **Comprensión de los datos**: exploración del dataset Oxford-IIIT Pet (distribución de clases, tamaños, calidad).
3. **Preparación de los datos**: redimensionamiento a 32x32 px, normalización y aplanado de imágenes.
4. **Modelamiento**: diseño y entrenamiento de un MLP con 2 capas ocultas (128 y 64 neuronas).
5. **Evaluación**: análisis de métricas (Accuracy, Precision, Recall, F1-Score, Matriz de Confusión) y de errores específicos.
6. **Despliegue**: no aplica en esta etapa del proyecto (evaluación académica).

## 7. Resultados y conclusiones

El modelo alcanzó un accuracy general de 69%, pero un análisis por clase reveló un sesgo 
importante: F1-Score de 0.81 para "perro" versus solo 0.12 para "gato", producto del 
desbalance de clases y de las limitaciones propias de un MLP para procesar imágenes (pérdida 
de información espacial al aplanar). Como mejoras futuras se propone aplicar balanceo de 
clases y considerar arquitecturas como CNN, que preservan la estructura espacial de la imagen.