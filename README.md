# 🧠 Reto 2 — Predicción de Venta Cruzada en Seguros de Salud

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15+-orange.svg)](https://tensorflow.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-yellow.svg)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.0+-green.svg)](https://xgboost.readthedocs.io/)
[![License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](#)

> **Curso:** Business Intelligence y Big Data (Nivel 5) | Odisea Data  
> **Reto:** Implementación de algoritmos avanzados de IA en Business Analytics  
> **Dataset:** [Health Insurance Cross Sell Prediction (Kaggle)](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction)  
> **Entorno:** Google Colab + Python 3.10+

---

## 🎯 Resumen

Modelo predictivo de **clasificación binaria** para identificar qué clientes de una compañía de seguros de salud tienen mayor probabilidad de contratar un seguro de vehículo (venta cruzada).

**Resultado principal:** modelo **LightGBM** con **AUC-ROC de 0.8574**, capaz de detectar el **91% de los clientes interesados**.

---

## 🏆 Resultados destacados

| Modelo | AUC-ROC | F1-score |
|---|---|---|
| 🥇 **LightGBM** | **0.8574** | 0.4383 |
| 🥈 XGBoost | 0.8568 | 0.4398 |
| 🥉 Random Forest | 0.8561 | 0.4358 |
| Logistic Regression | 0.8336 | 0.3988 |
| MLP Básico (Deep Learning) | 0.8197 | 0.3924 |
| MLP Profundo (Deep Learning) | 0.7705 | 0.3685 |

📊 **Comparativa visual:** [`outputs/charts/comparativa_final.png`](outputs/charts/comparativa_final.png)

---

## 🗺️ Pipeline del Proyecto

| # | Fase | Notebook |
|---|---|---|
| 1 | Selección del dataset | `data/raw/` |
| 2 | Preparación del entorno | `requirements.txt` |
| 3 | Exploración y EDA | [`notebooks/01_exploracion.ipynb`](notebooks/01_exploracion.ipynb) |
| 4 | Limpieza y transformación | [`notebooks/02_preparacion.ipynb`](notebooks/02_preparacion.ipynb) |
| 5a | Modelos ML clásico | [`notebooks/03_modelos_ml.ipynb`](notebooks/03_modelos_ml.ipynb) |
| 5b | Modelos Deep Learning | [`notebooks/04_modelos_deep_learning.ipynb`](notebooks/04_modelos_deep_learning.ipynb) |
| 6 | Evaluación | [`notebooks/03_modelos_ml.ipynb`](notebooks/03_modelos_ml.ipynb) |
| 7 | Interpretabilidad (SHAP) | [`notebooks/05_interpretabilidad.ipynb`](notebooks/05_interpretabilidad.ipynb) |
| 8 | Recomendaciones de negocio | [`reports/recomendaciones.md`](reports/recomendaciones.md) |

---

## 🔍 Hallazgos principales

### Top 3 variables más influyentes
1. **`Previously_Insured`** — Los clientes ya asegurados casi nunca contratan (tasa de conversión ~0.1%).
2. **`Vehicle_Damage`** — Los clientes con vehículo dañado convierten ~46 veces más.
3. **`Age`** — Los clientes entre 30 y 50 años muestran la mayor propensión.

### Insights de negocio
- ✅ **Excluir clientes ya asegurados** ahorra ~45% del coste de campaña.
- ✅ **Concentrar el 80% del esfuerzo comercial en el 11% de clientes** con mayor probabilidad.
- ✅ **Aplicar el modelo a otros productos** (hogar, vida) para escalar el ROI.

📊 **Informe completo:** [`reports/informe_analisis.md`](reports/informe_analisis.md)  
💼 **Recomendaciones de negocio:** [`reports/recomendaciones.md`](reports/recomendaciones.md)

---

## 📦 Estructura del proyecto

```text
reto2-ia-business-analytics/
├── data/              # Datasets (raw, processed, external)
├── notebooks/         # Jupyter Notebooks por fase (01-05)
├── scripts/           # Código reutilizable
├── models/            # Modelos entrenados y scalers
├── outputs/           # Gráficos, métricas y capturas
├── reports/           # Informes en Markdown
└── presentation/      # Presentación final
```

---

## 🚀 Cómo ejecutar

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

---

## 🛠️ Stack Tecnológico

- **Lenguaje:** Python 3.10+
- **Datos:** Pandas, NumPy
- **ML clásico:** Scikit-learn, XGBoost, LightGBM
- **Deep Learning:** TensorFlow, Keras
- **Interpretabilidad:** SHAP
- **Visualización:** Matplotlib, Seaborn

---

## 📦 Entregables

- [x] **1. Código del proyecto** → `notebooks/` y `scripts/`
- [x] **2. Informe del análisis** → [`reports/informe_analisis.md`](reports/informe_analisis.md)
- [x] **3. Modelo entrenado reutilizable** → `models/trained/`
- [x] **4. Presentación de resultados** → `presentation/`

---

## 👤 Autor

**Judit Giravent**  
Business Analytics Student | Odisea Data  
[LinkedIn](https://linkedin.com/in/judit-giravent-27b167156)

---

*Proyecto desarrollado como parte del curso Business Intelligence y Big Data de Odisea Data. Septiembre 2026.*