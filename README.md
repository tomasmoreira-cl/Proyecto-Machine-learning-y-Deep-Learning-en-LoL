# Proyecto-Machine-learning-y-Deep-Learning-en-LoL (in-progress)
Proyecto de análisis y predicción en League of Legends orientado a detectar las variables que influyen más en las victorias de cada partida. El objetivo es identificar factores de microjuego del jugador que impactan en el rendimiento y, a partir de ello, generar aprendizajes para aumentar las probabilidades de ganar partidas.

## Contenido
- Notebooks de jupyter que he utilizado para realizar los análisis descriptivos y modelos.
- Funciones auxiliares que utilicé dentro de los notebooks.
- Dataset de las partidas que analicé. En formato CSV y Excel.

## Uso
Descargar los dataset y ejecutar el código en Jupyter.

## Estado del proyecto
Actualmente:
- Limpieza del dataset ✅
- Exploración inicial de datos ✅
- Análisis descriptivo ✅ (en progreso)
- Modelamiento con machine learning y Deep Learning: Regresión logística, SVM con ajuste de hiperparámetros, Árboles de decisión, Random Forest, Red neuronal multicapa y XGBoosting. ❌
- Conclusiones finales. Predicción de victoria y microgame del jugador. ❌ 

## Próximos pasos
- Analizar las observaciones de la exploración de los datos y su análisis
- Rehacer comparativas el análisis descriptivo de mis partidas vs jugadores de mi elo y superior.
- Editar comentarios para que sea mas legible

---------------------

# 🏆 League of Legends AI Coach: Data-Driven Climbing Strategy

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Type](https://img.shields.io/badge/Type-Data%20Science%20Portfolio-orange)

> **Estado Actual:** 🚧 Proyecto en desarrollo activo. Fase de Análisis Descriptivo e Inferencial completada.

## 🎯 Objetivo del Proyecto
Este proyecto utiliza **Ciencia de Datos y Machine Learning** para auditar el rendimiento personal en *League of Legends*. El objetivo es identificar ineficiencias reales (gestión de oro, visión, champion pool) y desarrollar modelos predictivos que aumenten la probabilidad de victoria, eliminando mitos sobre el matchmaking mediante validación estadística.

## 📂 Contenido del Repositorio

El flujo de trabajo está dividido secuencialmente en la carpeta `Notebooks`:

| Archivo | Descripción |
| :--- | :--- |
| `01_extract_Flex_games.ipynb` | **Extracción ETL:** Conexión a la API de Riot para descargar el historial de partidas Flex. Genera `raw_flex.csv`. |
| `02_extract_SoloQ_games.ipynb` | **Extracción ETL:** Conexión a la API de Riot para descargar el historial de partidas SoloQ. Genera `raw_soloQ.csv`. |
| `03_EDA.ipynb` | **Análisis Principal:** Limpieza de datos, Feature Engineering (Rachas, Visión/Min), Tests de Hipótesis y generación del dataset maestro (`processed_data.csv`). |
| `funciones.py` | **Librería Auxiliar:** Contiene las funciones estadísticas (Mann-Whitney U) y de visualización reutilizables. |

## 📊 Hallazgos Clave (Fase 1)

Las conclusiones detalladas se encuentran al final del notebook `03_EDA.ipynb`. Algunos hallazgos estratégicos incluyen:

### 1. La Paradoja de la Visión
* **Flex Queue:** Se detectó una "Saturación Ineficiente". El volumen de wards es alto pero tiene **correlación nula ($p > 0.05$)** con la victoria.
* **Solo Queue:** La **calidad** de visión (`vs_per_min`) demostró ser estadísticamente significativa, validando una estrategia de "Calidad sobre Cantidad".

### 2. El "Muro" del Matchmaking
El análisis de series temporales confirmó un **Techo de Habilidad Rígido** tras 3 victorias consecutivas. El rendimiento individual colapsa en la 4ta partida debido al aumento de MMR, descartando factores psicológicos (Tilt) y validando la dificultad del sistema.

## 🛠️ Stack Tecnológico
* **Lenguaje:** Python.
* **Librerías:** Pandas, NumPy, SciPy (Estadística Inferencial), Matplotlib, Seaborn.
* **Datos:** Riot Games API (Match V5).

## 📂 Estructura de Archivos

```text
├── data/                   # Almacenamiento de datos
│   ├── processed_data.csv  # Dataset limpio y enriquecido (Listo para ML)
│   ├── raw_flex.csv        # Datos crudos Flex
│   └── raw_soloQ.csv       # Datos crudos SoloQ
├── Notebooks/              # Código fuente
│   ├── 01_extract_Flex_games.ipynb
│   ├── 02_extract_SoloQ_games.ipynb
│   ├── 03_EDA.ipynb
│   └── funciones.py
├── .gitignore
└── README.md
