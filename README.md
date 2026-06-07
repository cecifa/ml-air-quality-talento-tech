# 🌫️ Proyecto Integrador Machine Learning — Air Quality Predictor

Este repositorio contiene el desarrollo completo del Proyecto Integrador para el curso de **Machine Learning** de **Talento Tech / Buenos Aires Aprende** (Plan de Estudios 2026). 

El objetivo principal es abordar el ciclo de vida completo de un proyecto de aprendizaje automático: desde la ingesta, análisis exploratorio y preparación de los datos, hasta el entrenamiento, optimización y evaluación de modelos predictivos.

---

## 📊 Descripción del Problema y Dataset

El proyecto se basa en un **Dataset de Calidad del Aire** obtenido a través de Kaggle (datos consolidados de OpenAQ, AQICN y la EPA de EE. UU.). 

El objetivo ambiental y de análisis es predecir e identificar los factores que más influyen en el **Índice de Calidad del Aire (AQI)**, una métrica crítica para la salud pública y la toma de decisiones urbanas.

* **Variable Objetivo:** `AQI` (Air Quality Index) — Tarea de Regresión Continua (0 a 500).
* **Variables Predictoras:** Concentraciones de contaminantes atmosféricos (PM2.5, PM10, $O_3$, $NO_2$, CO, $SO_2$) y variables meteorológicas (Temperatura y Humedad).

---

## 📁 Estructura del Repositorio

El repositorio se organiza de forma modular para reflejar las distintas etapas del proceso formativo y de desarrollo:

```📁 ml-air-quality-talento-tech/
│
├── 📁 pre-entrega/       # Fase I: Preparación y Auditoría de Datos (Completado) [cite: 11]
│   ├── Pre-Entrega_Cecilia_Farías_-_Air_Quality_Dataset.ipynb
│   └── README.md         # Detalle técnico del EDA y la limpieza
│
└── 📁 entrega-final/     # Fase II: Modelado, Pipeline y Optimización (Próximamente) [cite: 8]
    ├── Entrega_Final_Air_Quality.ipynb
    └── README.md         # Conclusiones y comparación de modelos
