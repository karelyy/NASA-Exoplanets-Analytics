# 🌌 Análisis de Sistemas de Exoplanetas de la NASA
### Exploración de propiedades planetarias, patrones orbitales y predicciones mediante Machine Learning

Proyecto de análisis exploratorio de datos y Machine Learning enfocado en los registros de exoplanetas confirmados de la NASA. Mediante el uso de Python, métodos estadísticos y herramientas de visualización de datos, este proyecto investiga las características planetarias, sus relaciones con las estrellas anfitrionas y los factores asociados con la temperatura de equilibrio de los exoplanetas.

## 🎯 Objetivos del proyecto

- 🔭 Explorar las características físicas y orbitales de los exoplanetas descubiertos.
- 📊 Identificar relaciones estadísticas entre las propiedades planetarias y sus estrellas anfitrionas.
- 🪐 Analizar la distribución de exoplanetas entre los distintos sistemas estelares.
- 🤖 Desarrollar un modelo de Machine Learning para predecir la temperatura de equilibrio planetaria.

## 📁 Conjunto de datos

**Fuente:** [Exoplanetary Systems Discovered by NASA – Kaggle](https://www.kaggle.com/datasets/sathyanarayanrao89/nasa-exoplanetary-system/data)

**Fuente original de los datos:** [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/)

El conjunto de datos original contiene 32,552 registros y 93 variables, correspondientes a descubrimientos de exoplanetas realizados entre 1989 y 2022.

Después de seleccionar el conjunto de parámetros predeterminado (`default_flag = 1`), la base de datos analítica contiene:

| Característica | Registros |
|---|---:|
| Exoplanetas | 5,044 |
| Sistemas anfitriones únicos | 3,781 |
| Variables seleccionadas | 19 |
| Periodo de descubrimientos | 1989–2022 |

Cada fila de la base maestra representa un exoplaneta, identificado mediante `pl_name`, junto con información asociada a su sistema anfitrión (`hostname`).

## 🧹 Preparación de los datos

El proceso de preparación de los datos incluyó:

- Selección de variables relevantes para responder las preguntas de investigación.
- Filtrado de registros mediante `default_flag = 1`.
- Revisión de tipos de datos, valores faltantes y consistencia de las variables categóricas.
- Verificación de identificadores, relaciones entre variables y registros duplicados.
- Identificación de valores extremos y evaluación de su posible relevancia astronómica.

**Importante:** Los valores faltantes se conservaron en la base maestra. Se generaron subconjuntos analíticos de acuerdo con las variables requeridas para cada análisis.

## 🔎 Análisis exploratorio de datos (EDA)

El análisis se enfoca en cuatro áreas principales:

### 1. 🪐 Características planetarias

- Radio planetario (`pl_rade`).
- Masa planetaria (`pl_bmasse`).
- Temperatura de equilibrio (`pl_eqt`).
- Periodo orbital (`pl_orbper`).
- Excentricidad orbital (`pl_orbeccen`).

### 2. ⭐ Relaciones entre planetas y estrellas

- Masa estelar (`st_mass`).
- Radio estelar (`st_rad`).
- Temperatura efectiva estelar (`st_teff`).
- Relaciones entre las propiedades planetarias y estelares.

### 3. 🛰️ Dinámica orbital

- Periodo orbital vs. semieje mayor.
- Distancia orbital vs. temperatura de equilibrio.
- Excentricidad orbital vs. semieje mayor.

### 4. 🌠 Sistemas planetarios

- Número de planetas por sistema anfitrión (`sy_pnum`).
- Número de estrellas por sistema (`sy_snum`).
- Distribución de los planetas conocidos entre los distintos sistemas estelares.

## 📈 Principales hallazgos

### 1. Masa y radio planetarios

Se identificó una relación positiva entre la masa y el radio planetarios, a partir de 976 registros que contienen ambas mediciones.

| Método estadístico | Correlación |
|---|---:|
| Pearson (escala original) | 0.34 |
| Spearman | 0.78 |
| Pearson (escala logarítmica) | 0.84 |

Los resultados sugieren una relación monotónica positiva fuerte, que se hace más evidente después de aplicar una transformación logarítmica. La dispersión observada podría reflejar diferencias en la composición de los planetas y en los métodos utilizados para medir sus propiedades.

### 2. Distancia orbital y temperatura de equilibrio

Se observó una correlación negativa de Spearman de **-0.50** entre la distancia orbital y la temperatura de equilibrio.

El análisis visual destaca una concentración de planetas calientes en órbitas cercanas, incluidos los denominados *Júpiteres calientes* (*Hot Jupiters*), así como la presencia de algunos planetas grandes y distantes con temperaturas elevadas.

### 3. Excentricidad orbital

El análisis revela distintos patrones orbitales dentro de la población observada. Muchos planetas en órbitas cercanas presentan baja excentricidad, mientras que algunos planetas más distantes muestran órbitas considerablemente más elípticas.

### 4. Valores extremos y distribución de los datos

Las propiedades planetarias presentan rangos amplios y distribuciones asimétricas. Las observaciones extremas se investigaron como posibles casos astronómicos relevantes, en lugar de clasificarlas automáticamente como registros erróneos.

## 🤖 Machine Learning — Random Forest Regressor

Se desarrolló un modelo de regresión Random Forest para predecir la temperatura de equilibrio planetaria (`pl_eqt`) a partir de características planetarias y estelares seleccionadas.

### Preparación de los datos

| Etapa | Registros |
|---|---:|
| Conjunto de datos inicial | 5,044 |
| Registros después de eliminar valores faltantes (NaN) | 766 |
| Datos conservados | 15.2 % |

Se aplicó un filtrado de casos completos (*complete-case filtering*), eliminando los registros que presentaban valores faltantes en las variables seleccionadas para el modelo.

### Configuración del modelo

- **Algoritmo:** Random Forest Regressor.
- **Variable objetivo:** Temperatura de equilibrio planetaria (`pl_eqt`).
- **División de datos:** 80 % entrenamiento / 20 % prueba.
- **Registros de entrenamiento:** 612.
- **Registros de prueba:** 154.

### Desempeño del modelo

| Métrica de evaluación | Resultado |
|---|---:|
| R² (Coeficiente de determinación) | 0.934 |
| Error cuadrático medio (MSE) | 21,539.515 |
| Raíz del error cuadrático medio (RMSE) | 146.76 K |

### Resultados preliminares

El modelo obtuvo un R² de **0.934**, lo que indica que explicó aproximadamente el 93.4 % de la variabilidad de la temperatura de equilibrio dentro de la muestra de prueba.

El RMSE, de aproximadamente **146.76 K**, representa la magnitud típica de los errores de predicción, expresada en Kelvin.

Las predicciones mostraron desviaciones menores en varias observaciones de temperatura media y alta, mientras que algunos planetas más fríos presentaron errores de mayor magnitud.

### Limitaciones y consideraciones

- Después de eliminar los registros con valores faltantes, se conservó únicamente el 15.2 % del conjunto de datos inicial.
- El tamaño reducido de la muestra podría limitar la representatividad del modelo respecto a la población general de exoplanetas.
- El desempeño del modelo depende de las variables seleccionadas y de su disponibilidad.
- Random Forest permite capturar relaciones no lineales, pero no establece relaciones de causalidad física.
- Se recomienda realizar validaciones adicionales, analizar la importancia de las variables y aplicar validación cruzada para evaluar la robustez del modelo.

*Las métricas reportadas corresponden a la muestra de prueba evaluada y no deben interpretarse como evidencia de capacidad de generalización a todos los exoplanetas conocidos. El desempeño del modelo debe analizarse considerando la estrategia de validación, el tamaño de la muestra y los posibles sesgos observacionales.*

## 🛠️ Tecnologías y bibliotecas utilizadas

- 🐍 **Python:** Análisis de datos y desarrollo del modelo.
- 🐼 **Pandas:** Manipulación y preparación de datos.
- 🔢 **NumPy:** Operaciones numéricas.
- 📊 **Matplotlib y Seaborn:** Visualización estadística.
- 📈 **Plotly:** Visualizaciones interactivas.
- 🧪 **SciPy:** Análisis estadístico y métodos de correlación.
- 🤖 **Scikit-learn:** Desarrollo de modelos de Machine Learning.

## ⚠️ Limitaciones del análisis

- No todos los parámetros planetarios están disponibles para cada registro.
- Algunos análisis utilizan subconjuntos más pequeños debido a la ausencia de determinadas mediciones.
- Los valores de masa planetaria pueden representar la masa real o la masa proyectada (M × sin(i)), dependiendo del método de medición.
- Los sesgos observacionales y de detección influyen en la población de exoplanetas conocidos.
- Correlación no implica causalidad.
- El número de planetas conocidos en un sistema no necesariamente representa la cantidad total de planetas que existen en él.

## 📂 Estructura del repositorio

```text
exoplanetary-systems-analytics/
│
├── README.md
├── requirements.txt
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── exoplanetary_systems_analytics.ipynb
│   └── exoplanetary_systems_ml.ipynb
│
└── outputs/
    ├── figures/
    ├── interactive/
    └── reports/
```

## 🚀 Propósito del proyecto

Este proyecto integra mi formación en ingeniería con mi experiencia en desarrollo de habilidades de Data Analytics y Data Science. Demuestra un flujo de trabajo analítico de principio a fin, desde la comprensión y preparación de los datos hasta la exploración estadística, visualización y modelado predictivo.

**Autora:** Lilian Karely Martínez  
**Proyecto:** NASA Exoplanets Analytics  
**Fecha:** Noviembre de 2026
