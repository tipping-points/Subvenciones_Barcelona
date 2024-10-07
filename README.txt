1. Introducción
El propósito de este proyecto es analizar y predecir las subvenciones otorgadas por el Ayuntamiento de Barcelona para el año 2025. Los datos utilizados incluyen variables como Import_Sollicitat (monto solicitado), Import_Atorgat_Inicial (monto otorgado inicialmente), características temporales (fechas de convocatoria y otorgamiento), tipos de subvenciones, y otras características relacionadas con el beneficiario y la gestión de la subvención.

El objetivo principal es construir un modelo predictivo que estime el monto de las subvenciones en 2025 y determine qué convocatorias tendrán mayor importancia en ese año, basado en tendencias pasadas y características relevantes.

2. Depuración de datos
a. Eliminación de valores negativos
Se realizó una limpieza de datos para eliminar cualquier valor negativo de las columnas relevantes (principalmente los montos de subvención). Solo se consideraron números positivos para asegurar la consistencia y lógica de las subvenciones.

b. Preprocesamiento y selección de variables
Se analizaron todas las variables de entrada (features) y la variable objetivo (Import_Atorgat_Inicial).
Se revisaron las distribuciones de las variables y se eliminaron las que presentaban datos inconsistentes o con valores no aplicables para el modelo predictivo.
Se llevaron a cabo estrategias de imputación de valores nulos, y se realizó codificación de variables categóricas para su uso en modelos de machine learning.
c. Análisis de correlación
Se realizó un análisis de correlación para evaluar la relación entre las variables numéricas. Se observó una correlación alta (0.87) entre Import_Sollicitat y Import_Atorgat_Inicial, lo que llevó a considerar la posible eliminación de Import_Sollicitat del modelo para reducir la colinealidad. Esta decisión se tomará en función de si su inclusión mejora la precisión del modelo.

3. Resultados
a. Entrenamiento del modelo
Se entrenaron varios modelos de machine learning para identificar el que proporcionaba el mejor rendimiento. Estos modelos incluyeron:

Random Forest (el modelo con mejor desempeño).
Regresión Lineal.
XGBoost.
CatBoost.
El modelo Random Forest mostró los mejores resultados en términos de precisión (R² score) y error (MAE, MSE).

b. Optimización de hiperparámetros
Se aplicó optimización bayesiana a los hiperparámetros del modelo Random Forest para maximizar su rendimiento predictivo. Los mejores parámetros encontrados fueron:

n_estimators: 172
max_depth: 29
min_samples_leaf: 1
min_samples_split: 2
c. Evaluación de la importancia de las características
Se analizó la importancia de las variables (feature importance) en el modelo final optimizado. Import_Sollicitat resultó ser la característica con mayor influencia en las predicciones, seguida por Entitat_Municipal y Tipologia_De_Subvencio.

d. Predicciones y gráficos
Se generaron visualizaciones para entender los resultados de las predicciones:

Evolución del Monto Total de Subvenciones: Se mostró cómo se comportaron las subvenciones a lo largo de los años y la proyección para 2025.
Distribución de las Predicciones para 2025: La mayoría de las subvenciones para 2025 se agrupan en montos bajos (menores a 0.05 millones de euros).
Comparación de Predicciones vs. Valores Reales: Se observó una relación lineal positiva entre las predicciones y los valores reales, validando la capacidad del modelo para ajustarse bien a los datos históricos.
4. Conclusiones
Import_Sollicitat como variable predictiva: Se identificó como la característica más influyente para predecir el monto de subvención, pero dado su alto grado de correlación con Import_Atorgat_Inicial, se sugirió evaluar su inclusión basada en los resultados finales.
Modelo Random Forest: Fue el modelo con mejor desempeño y, tras la optimización de hiperparámetros, se obtuvieron métricas de error satisfactorias y una buena capacidad de predicción.
Predicción para 2025: Se logró una predicción razonable del monto total de subvenciones y su distribución para el año 2025.
Análisis adicional: La evaluación de la importancia de características y correlaciones permitió identificar las variables clave que más afectan el modelo, orientando la selección de features y la interpretación de los resultados finales.