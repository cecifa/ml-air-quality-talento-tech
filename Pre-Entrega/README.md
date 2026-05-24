# 🌫️ Air Quality Dataset — Pre-Entrega ML

Proyecto desarrollado en el marco del curso de **Machine Learning** de [Talento Tech](https://buenosairesaprende.com.ar/) (Plan de Estudios 2026), correspondiente a la **Pre-Entrega** del Proyecto Integrador.

---

## 📋 Descripción

Análisis exploratorio y preprocesamiento de un dataset de calidad del aire con el objetivo de preparar los datos para la etapa de modelado. El dataset contiene mediciones de contaminantes atmosféricos (PM2.5, PM10, NO₂, SO₂, CO, O₃) e índice de calidad del aire (AQI) para distintas ciudades.

**Variable objetivo:** `AQI` (Air Quality Index) — regresión continua (0 a 500).

---

## 📂 Estructura del proyecto

```
📁 pre-entrega-air-quality/
│
├── Pre-Entrega_Cecilia_Farías_-_Air_Quality_Dataset.ipynb   # Notebook principal
└── README.md
```

---

## 🗂️ Dataset

- **Fuente:** [Air Quality Dataset — Kaggle](https://www.kaggle.com/datasets/price438/air-quality-dataset)
- **Origen de los datos:** OpenAQ, AQICN y EPA de Estados Unidos
- **Características:** ~columnas de contaminantes, condiciones meteorológicas, ciudad y fecha
- **Importación:** via `kagglehub` directamente desde Kaggle

| Variable | Descripción | Unidad |
|---|---|---|
| AQI | Índice de Calidad del Aire | 0–500 |
| PM2.5 | Micropartículas ≤ 2.5 µm | µg/m³ |
| PM10 | Partículas ≤ 10 µm | µg/m³ |
| Ozone | Concentración de ozono | ppb |
| NO2 | Dióxido de nitrógeno | ppb |
| CO | Monóxido de carbono | ppm |
| SO2 | Dióxido de azufre | ppb |
| Temperature | Temperatura | — |
| Humidity | Humedad relativa | — |
| City | Ciudad de la medición | — |
| Date | Fecha del registro | — |

---

## 🔍 Etapas del notebook

### 1. Análisis Exploratorio (EDA)
- Inspección general: shape, tipos de datos, estadísticas descriptivas
- Distribución de variables numéricas (histogramas, KDE)
- Análisis por ciudad: mediciones, comparativa AQI entre ciudades (boxplots)
- Variación estacional del AQI por mes (paleta semáforo: verde → rojo según contaminación)
- Detección de outliers (boxplot horizontal)
- Mapa de calor de valores nulos

### 2. Limpieza de datos
- Eliminación de filas con `AQI` nulo (variable objetivo), preservando el resto del dataset
- Auditoría completa de nulos por columna (cantidad y porcentaje)

### 3. Transformaciones
- Conversión de fechas y extracción de `Año` y `Mes` como variables numéricas
- One-Hot Encoding de la variable `City` (dummies con prefijo `City_`)
- Experimento comparativo de escalado sobre AQI: MinMaxScaler vs StandardScaler
- Estandarización definitiva (StandardScaler) de las 8 variables ambientales predictoras

### 4. Selección de variables
- Se excluyen identificadores y la fecha nativa (`Date`)
- Se conservan variables numéricas continuas, discretas y dummies

### 5. División train/test
- Split 80% entrenamiento / 20% prueba con `random_state=42`
- Verificación de dimensiones y estadísticas del target en cada conjunto

---

## 🛠️ Tecnologías utilizadas

- Python 3
- pandas, numpy
- matplotlib, seaborn
- scipy, scikit-learn (`MinMaxScaler`, `StandardScaler`, `train_test_split`)
- kagglehub
- Google Colab

---

## ▶️ Cómo ejecutar

1. Abrir el notebook en [Google Colab](https://colab.research.google.com/)
2. Ejecutar todas las celdas en orden (`Runtime → Run all`)
3. El dataset se descarga automáticamente desde Kaggle via `kagglehub` (requiere cuenta de Kaggle configurada)

---

## 📌 Próximos pasos (Entrega Final)

- Entrenamiento y evaluación de modelos supervisados (Regresión Lineal, KNN, Random Forest)
- Optimización de hiperparámetros con GridSearchCV
- Implementación de pipeline completo con scikit-learn
- Comunicación de resultados

---

*Curso: Machine Learning — Talento Tech / Buenos Aires Aprende (2026)*
