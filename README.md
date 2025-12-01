# 🏆 Auditoria de Gamplay en League of Legends: Estrategia de ascenso basada en datos

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Status](https://img.shields.io/badge/Status-Phase%201%20Completed-green)
![Type](https://img.shields.io/badge/Type-Data%20Analysis-orange)

## 🎯 Objetivo del Proyecto
Realizar una **auditoría estadística y predictiva** del rendimiento personal en *League of Legends*. El proyecto utiliza un enfoque híbrido:

1.  **Análisis Inferencial (EDA):** Para identificar ineficiencias tácticas (gestión de oro, visión, champion pool) y desmitificar patrones del matchmaking mediante validación estadística.
2.  **Machine Learning:** Para entrenar modelos supervisados capaces de **clasificar resultados y predecir victorias**, determinando matemáticamente qué variables (features) tienen mayor peso predictivo en el desenlace de la partida.

> **Estado Actual:** 🚧 Proyecto en desarrollo. Fase de Análisis Descriptivo e Inferencial completada; Modelado Predictivo en curso.

## 📂 Contenido del Repositorio

El flujo de trabajo y las conclusiones detalladas se encuentran en la carpeta `notebooks`:

| Archivo | Descripción |
| :--- | :--- |
| `01_extract_Flex_games.ipynb` | **Extracción ETL:** Script de conexión a la Riot API para descargar historial de partidas Flex. |
| `02_extract_SoloQ_games.ipynb` | **Extracción ETL:** Script de conexión a la Riot API para descargar historial de partidas SoloQ. |
| `03_EDA.ipynb` | **Análisis Principal:** Limpieza, Feature Engineering, Tests de Hipótesis y generación del dataset maestro. **Contiene el diagnóstico de Visión, Rachas y Champion Pool.** |
| `funciones.py` | **Librería Auxiliar:** Funciones reutilizables para tests estadísticos y gráficos. |

## 📊 Hallazgos Clave (Fase 1: EDA e Inferencia)

### 1. Eficiencia de la Visión (Flex vs SoloQ)
Mediante tests de hipótesis (Inferencial), se descubrió una divergencia estratégica:
* **En Flex Queue:** El volumen de visión no correlaciona con la victoria ($p > 0.05$), indicando una saturación de recursos ineficiente.
* **En Solo Queue:** La calidad de visión (`vs_per_min`) demostró ser estadísticamente significativa ($p < 0.01$), validando que en el juego individual la precisión supera a la cantidad.

### 2. Análisis de Rendimiento por Campeón (Champion Pool)
Se evaluó el Win Ratio histórico para depurar la cartera de campeones:
* **Activos:** Sejuani, Jarvan IV y Malphite (WR > 55%).
* **Pasivos:** Trundle y Soportes defensivos (WR < 48%).

### 3. Elasticidad del Matchmaking ("El Muro de las 3 Victorias")
El análisis de series temporales reveló un **Techo de Habilidad** tras rachas de 3 victorias consecutivas, donde la probabilidad de ganar la 4ta partida cae drásticamente. El análisis de métricas individuales bajo presión descartó factores psicológicos, apuntando a un aumento de dificultad del MMR como causa principal.

### 4. Matriz de Correlación
El análisis de correlación reveló lo siguiente:

1.  **En SoloQ:** Mis juego se deciden en los primeros 15 minutos. La estrategia óptima es **Agresiva/Snowball**. Debo priorizar campeones de *Early/Mid Game* que puedan ganar línea y convertir ese oro en KDA rápidamente, ya que el sistema no perdona las desventajas económicas.

2.  **En Flex:** El juego es permisivo. La estrategia óptima es **Coordinada/Scaling**. Puedo permitirme perder línea levemente si eso garantiza mejor peleas de equipo (*Teamfighting*) tarde, ya que el oro temprano no dicta la sentencia final.

3.  **Gestión de Expectativas:** Debo asumir que tras una racha positiva, la siguiente partida tendrá una probabilidad base de victoria menor debido al ajuste de MMR, independientemente de mi desempeño.
   
----
## 🛠️ Stack Tecnológico
* **Lenguaje:** Python.
* **Librerías:** Pandas, NumPy, SciPy (Estadística Inferencial), Matplotlib, Seaborn.
* **Datos:** Riot Games API (Match V5).
  
---
## 🚀 Instrucciones de Uso
1.  Clonar el repositorio.
2.  Instalar dependencias: `pip install -r requirements.txt`
3.  Ejecutar los notebooks en orden numérico para reproducir el pipeline.

---
## 📅 Roadmap (Próximas Etapas)
- [ ] **Fase 2: Modelado Predictivo:** Implementación de algoritmos (XGBoost, Regresión, Random Forest, Red neuronal y SVM) para estimar probabilidad de victoria pre-partida.
- [ ] **Fase 3: Optimización:** Tuning de hiperparámetros y selección de features basada en importancia (Feature Importance).

---
**Autor:** Tomás Moreira | [LinkedIn](https://www.linkedin.com/in/tomas-moreira/)
