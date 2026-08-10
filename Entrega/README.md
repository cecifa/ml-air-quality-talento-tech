# 🌫️ Air Quality Dataset — Proyecto Final ML

Proyecto desarrollado en el marco del curso de **Machine Learning** de [Talento Tech](https://buenosairesaprende.com.ar/) (Plan de Estudios 2026). Abarca el ciclo completo de un proyecto de ML: desde el análisis exploratorio hasta el entrenamiento, evaluación y validación cruzada del modelo.

---

## 📋 Descripción

Análisis y modelado de un dataset de calidad del aire con el objetivo de **predecir el Índice de Calidad del Aire (AQI)**, una variable continua en escala de 0 a 500. El dataset contiene mediciones de contaminantes atmosféricos (PM2.5, PM10, NO₂, SO₂, CO, O₃) y condiciones meteorológicas para distintas ciudades de Estados Unidos.

**Tipo de problema:** Regresión supervisada  
**Variable objetivo:** `AQI` (Air Quality Index)  
**Modelo elegido:** Random Forest Regressor

---

## 📂 Estructura del proyecto

```
📁 ml-air-quality-talento-tech/
│
├── Entrega_Cecilia_Farías_Air_Quality_Dataset.ipynb        # Notebook entrega final
├── Pre-Entrega_Cecilia_Farías_-_Air_Quality_Dataset.ipynb  # Notebook pre-entrega
└── README.md
```

---

## 🗂️ Dataset

- **Fuente:** [Air Quality Dataset — Kaggle](https://www.kaggle.com/datasets/price438/air-quality-dataset)
- **Origen de los datos:** OpenAQ, AQICN y EPA de Estados Unidos
- **Importación:** via `kagglehub` directamente desde Kaggle

| Variable | Descripción | Unidad |
|---|---|---|
| AQI | Índice de Calidad del Aire (variable objetivo) | 0–500 |
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
- Distribución de variables numéricas (histogramas con KDE)
- Análisis por ciudad: ranking de contaminación, comparativa AQI entre ciudades
- Variación estacional del AQI por mes (boxplot con paleta semáforo)
- Scatter plot temperatura vs. ozono
- Detección de outliers en AQI
- Mapa de calor de valores nulos

**Hallazgos clave del EDA:**
- Distribuciones con fuerte sesgo positivo en contaminantes → justifica imputación por mediana
- Correlación negativa alta entre Temperature y Humidity (r = -0.84) → multicolinealidad
- Eventos extremos aislados de AQI cercanos a 500 → justifica algoritmo robusto a outliers
- Los Ángeles presenta peor calidad de aire promedio; la ciudad es variable predictora relevante

### 2. Limpieza de datos
- Eliminación de filas con `AQI` nulo (variable objetivo)
- Auditoría completa de nulos por columna (cantidad y porcentaje)

### 3. Transformaciones (antes del split)
- Conversión de fechas y extracción de `Año` y `Mes` como variables numéricas
- One-Hot Encoding de la variable `City` (dummies con prefijo `City_`)
- Experimento comparativo MinMaxScaler vs. StandardScaler

### 4. División train/test
- Split 80% entrenamiento / 20% prueba con `random_state=42`
- Verificación de consistencia de distribuciones entre conjuntos (KDE comparativo)

### 5. Transformaciones (después del split, evitando data leakage)
- Imputación con mediana calculada **únicamente sobre X_train**, aplicada a ambos sets
- Estandarización Z-score calculada **únicamente sobre X_train**, aplicada a ambos sets

### 6. Entrenamiento del modelo
- **Random Forest Regressor** (`n_estimators=100`, `random_state=42`)
- Justificación: robusto a multicolinealidad, captura relaciones no lineales, tolerante a outliers

### 7. Evaluación

| Métrica | Resultado |
|---|---|
| MAE (Error Absoluto Medio) | ~7.58 puntos de AQI |
| R² (Coeficiente de Determinación) | ~0.7948 |

### 8. Validación cruzada
- Pipeline con imputación + escalado + modelo para evitar data leakage entre folds
- 5-Fold Cross-Validation → R² promedio robusto y consistente entre los 5 pliegues

---

## 🛠️ Tecnologías utilizadas

- Python 3
- pandas, numpy
- matplotlib, seaborn
- scipy
- scikit-learn (`RandomForestRegressor`, `Pipeline`, `cross_val_score`, `SimpleImputer`, `StandardScaler`, `train_test_split`)
- kagglehub
- Google Colab

---

## ▶️ Cómo ejecutar

1. Abrir el notebook en [Google Colab](https://colab.research.google.com/)
2. Ejecutar todas las celdas en orden (`Runtime → Run all`)
3. El dataset se descarga automáticamente desde Kaggle via `kagglehub` (requiere cuenta de Kaggle configurada en el entorno)

---

## 💡 Conclusiones

El modelo Random Forest alcanzó un R² de ~0.79 en el set de prueba, explicando casi el 80% de la variabilidad del AQI, con un error promedio de 7.58 puntos de índice. La validación cruzada confirmó la estabilidad del modelo a través de distintas particiones del dataset. Como mejora futura se propone enriquecer el dataset balanceando el volumen de registros por ciudad.

---

*Curso: Machine Learning — Talento Tech / Buenos Aires Aprende (2026)*
