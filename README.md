# 🧠 Reto 2 — Predicción de Venta Cruzada en Seguros de Salud

> **Curso:** Business Intelligence y Big Data (Nivel 5) | Odisea Data  
> **Reto:** Implementación de algoritmos avanzados de IA en Business Analytics  
> **Dataset:** [Health Insurance Cross Sell Prediction (Kaggle)](https://www.kaggle.com/anmolkumar/health-insurance-cross-sell-prediction)  
> **Entorno:** Google Colab + Python 3.10+

## 📌 Descripción del Proyecto

Una compañía de seguros de salud desea optimizar su estrategia de **venta cruzada** ofreciendo seguros de vehículo a sus clientes actuales. El objetivo de este proyecto es construir un **modelo predictivo de clasificación binaria** que identifique qué asegurados tienen mayor probabilidad de estar interesados en adquirir una póliza de automóvil.

Este tipo de modelo permite a la empresa:

- **Dirigir sus campañas de marketing** únicamente a los clientes con mayor propensión a la compra.
- **Reducir costes de comunicación** y mejorar el retorno de la inversión (ROI).
- **Optimizar su modelo de negocio** y aumentar los ingresos por venta cruzada.

El dataset contiene **381.109 registros** de clientes con seguros de salud, con **12 variables** que incluyen datos demográficos, información sobre el vehículo, historial de seguros y el canal de contacto.

## 🎯 Objetivos del Proyecto

1. **Explorar y comprender** el dataset: estructura, variables clave, análisis descriptivo y detección de desbalanceo de clases.
2. **Preparar y limpiar** los datos: tratamiento de valores nulos, atípicos, codificación de variables categóricas y escalado.
3. **Desarrollar modelos avanzados de IA**: Random Forest, Gradient Boosting (XGBoost/LightGBM) y redes neuronales profundas.
4. **Evaluar y comparar** los modelos con métricas robustas para datos desbalanceados: **F1-score, Recall y AUC-ROC**.
5. **Extraer insights de negocio** e interpretar los resultados con técnicas como **SHAP** y **LIME**.
6. **Generar recomendaciones prácticas** para la toma de decisiones.

## 📊 Variables del Dataset

| Variable | Descripción |
|---|---|
| `id` | Identificador único del cliente |
| `Gender` | Género del cliente |
| `Age` | Edad del cliente |
| `Driving_License` | 0: No tiene carné, 1: Tiene carné |
| `Region_Code` | Código de la región del cliente |
| `Previously_Insured` | 1: Ya tiene seguro de vehículo, 0: No tiene |
| `Vehicle_Age` | Antigüedad del vehículo |
| `Vehicle_Damage` | 1: Ha sufrido daños, 0: No ha sufrido daños |
| `Annual_Premium` | Prima anual que paga el cliente |
| `PolicySalesChannel` | Canal de contacto (anónimo) |
| `Vintage` | Días de antigüedad del cliente en la compañía |
| `Response` | **Variable objetivo:** 1: Interesado, 0: No interesado |

## 🛠️ Stack Tecnológico

- **Lenguaje:** Python 3.10+
- **Manipulación de datos:** Pandas, NumPy
- **Visualización:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn, XGBoost, LightGBM
- **Deep Learning:** TensorFlow / Keras
- **Interpretabilidad:** SHAP, LIME
- **Entorno:** Google Colab

## 📁 Estructura del Proyecto

```text
reto2-ia-business-analytics/
├── data/                  # Datasets (raw, processed, external)
├── notebooks/             # Jupyter Notebooks por fase
├── scripts/               # Código reutilizable (preprocess, train, evaluate)
├── models/                # Modelos entrenados y scalers
├── outputs/               # Gráficos, métricas y capturas de pantalla
├── reports/               # Informes en Markdown
└── presentation/          # Presentación final de resultados
```

## 🗺️ Fases del Proyecto

| # | Fase | Notebook |
|---|------|----------|
| 1 | Selección del dataset | `data/raw/` |
| 2 | Preparación del entorno | `requirements.txt` |
| 3 | Importación y exploración | `notebooks/01_exploracion.ipynb` |
| 4 | Limpieza y transformación | `notebooks/02_preparacion.ipynb` |
| 5 | Modelos avanzados de IA | `notebooks/03_modelos_ml.ipynb` y `notebooks/04_modelos_deep_learning.ipynb` |
| 6 | Evaluación de modelos | `notebooks/05_evaluacion.ipynb` |
| 7 | Interpretación de resultados | `outputs/charts/` y `reports/analisis_kpi.md` |
| 8 | Recomendaciones | `reports/recomendaciones.md` |

## 📈 Resultados Esperados

- **Modelo con mejor rendimiento:** XGBoost o Random Forest, con un **AUC-ROC superior a 0.85**.
- **Variables más influyentes:** `Previously_Insured`, `Vehicle_Damage` y `Age`.
- **Recomendaciones de negocio:** Estrategias de contacto segmentadas por perfil de cliente y canal óptimo.

## 🚀 Cómo Ejecutar

### En Google Colab

1. Abre el notebook deseado desde `notebooks/`.
2. Súbelo a Colab (`Archivo > Subir notebook`).
3. Ejecuta las celdas en orden.

### En local

```bash
git clone https://github.com/jdthgp27/reto2-ia-business-analytics.git
cd reto2-ia-business-analytics
python -m venv venv
source venv/Scripts/activate   # Windows
pip install -r requirements.txt
jupyter notebook
```

## 📦 Entregables

- [ ] **1. Código del proyecto** → `scripts/` y `notebooks/`
- [ ] **2. Informe del análisis** → `reports/informe_analisis.md`
- [ ] **3. Modelo entrenado reutilizable** → `models/trained/`
- [ ] **4. Presentación de resultados** → `presentation/`

## 👤 Autor

**Judit Giravent**  
Business Analytics Student | Odisea Data