# 🧠 Reto 2 — Predicción de Venta Cruzada en Seguros de Salud

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15+-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](https://tensorflow.org/)
[![Keras](https://img.shields.io/badge/Keras-2.x-D00000?style=for-the-badge&logo=keras&logoColor=white)](https://keras.io/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.0+-189FDD?style=for-the-badge)](https://xgboost.readthedocs.io/)
[![LightGBM](https://img.shields.io/badge/LightGBM-4.x-02569B?style=for-the-badge)](https://lightgbm.readthedocs.io/)
[![SHAP](https://img.shields.io/badge/SHAP-0.44+-8A2BE2?style=for-the-badge)](https://shap.readthedocs.io/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Completado-success?style=for-the-badge)]()

> **Curso:** Business Intelligence y Big Data (Nivel 5) | Odisea Data
> **Reto:** Implementación de algoritmos avanzados de IA en Business Analytics
> **Dataset:** [Health Insurance Cross Sell Prediction (Kaggle)](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction)
> **Entorno:** Google Colab + Python 3.10+

---

## 🎯 Resumen

Modelo predictivo de **clasificación binaria** para identificar qué clientes de una compañía de seguros de salud tienen mayor probabilidad de contratar un seguro de vehículo (**venta cruzada**).

**Resultado principal:** modelo **LightGBM** con **AUC-ROC de 0,8574**, capaz de detectar el **91% de los clientes interesados**.

---

## 🏆 Resultados destacados

| Modelo | AUC-ROC | F1-score |
|---|---:|---:|
| 🥇 **LightGBM** | **0,8574** | 0,4383 |
| 🥈 XGBoost | 0,8568 | 0,4398 |
| 🥉 Random Forest | 0,8561 | 0,4358 |
| Logistic Regression | 0,8336 | 0,3988 |
| MLP Básico (Deep Learning) | 0,8197 | 0,3924 |
| MLP Profundo (Deep Learning) | 0,7705 | 0,3685 |

📊 **Comparativa visual:** ![Comparativa final](outputs/charts/comparativa_final.png)

---

## 🗺️ Pipeline del proyecto

| # | Fase | Notebook / Ubicación |
|---|---|---|
| 1 | Selección del dataset | `data/raw/` |
| 2 | Preparación del entorno | `requirements.txt` |
| 3 | Exploración y EDA | [notebooks/01_exploracion.ipynb](notebooks/01_exploracion.ipynb) |
| 4 | Limpieza y transformación | [notebooks/02_preparacion.ipynb](notebooks/02_preparacion.ipynb) |
| 5a | Modelos ML clásicos | [notebooks/03_modelos_ml.ipynb](notebooks/03_modelos_ml.ipynb) |
| 5b | Modelos Deep Learning | [notebooks/04_modelos_deep_learning.ipynb](notebooks/04_modelos_deep_learning.ipynb) |
| 6 | Evaluación comparativa | [notebooks/03_modelos_ml.ipynb](notebooks/03_modelos_ml.ipynb) |
| 7 | Interpretabilidad (SHAP) | [notebooks/05_interpretabilidad.ipynb](notebooks/05_interpretabilidad.ipynb) |
| 8 | Recomendaciones de negocio | [reports/recomendaciones.md](reports/recomendaciones.md) |

---

## 🔍 Hallazgos principales

### Top 3 variables más influyentes

1. **`Previously_Insured`** — Los clientes ya asegurados casi nunca contratan (tasa de conversión ~0,1%).
2. **`Vehicle_Damage`** — Los clientes con vehículo dañado convierten **~46 veces más**.
3. **`Age`** — Los clientes entre 30 y 50 años muestran la mayor propensión.

### Insights de negocio

- ✅ **Excluir clientes ya asegurados** ahorra ~45% del coste de campaña.
- ✅ **Concentrar el 80% del esfuerzo comercial en el 11% de clientes** con mayor probabilidad.
- ✅ **Aplicar el modelo a otros productos** (hogar, vida) para escalar el ROI.

📊 **Informe completo:** [reports/informe_analisis.md](reports/informe_analisis.md)
💼 **Recomendaciones de negocio:** [reports/recomendaciones.md](reports/recomendaciones.md)
📈 **Análisis de KPIs:** [reports/analisis_kpi.md](reports/analisis_kpi.md)

---

## 📦 Estructura del proyecto

```
reto2-ia-business-analytics/
│
├── data/
│   ├── raw/                          # Dataset original de Kaggle
│   ├── processed/                    # Datasets procesados (train/test)
│   └── external/                     # Datos externos (train.csv)
│
├── notebooks/                        # Jupyter Notebooks por fase
│   ├── 01_exploracion.ipynb
│   ├── 02_preparacion.ipynb
│   ├── 03_modelos_ml.ipynb
│   ├── 04_modelos_deep_learning.ipynb
│   └── 05_interpretabilidad.ipynb
│
├── scripts/                          # Código reutilizable
│
├── models/
│   ├── trained/                      # Modelos entrenados (.pkl, .keras)
│   │   ├── lightgbm.pkl
│   │   ├── xgboost.pkl
│   │   ├── random_forest.pkl
│   │   ├── logistic_regression.pkl
│   │   ├── mlp_basico.keras
│   │   └── mlp_profundo.keras
│   └── scalers/
│       └── scaler.pkl
│
├── outputs/
│   ├── charts/                       # 17 gráficos PNG
│   ├── metrics/                      # 5 CSVs con métricas
│   └── screenshots/
│
├── reports/                          # Informes (MD + PDF)
│   ├── informe_analisis.md / .pdf
│   ├── recomendaciones.md / .pdf
│   └── analisis_kpi.md / .pdf
│
├── presentation/                     # Presentación final (PPTX)
│
├── requirements.txt
├── .env.example
├── .gitignore
├── LICENSE
└── README.md
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
source venv/Scripts/activate   # Windows (Git Bash)
# source venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
jupyter notebook
```

---

## 🛠️ Stack tecnológico

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/scikit--learn-1.3+-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="scikit-learn"/>
  <img src="https://img.shields.io/badge/XGBoost-2.0+-189FDD?style=for-the-badge" alt="XGBoost"/>
  <img src="https://img.shields.io/badge/LightGBM-4.x-02569B?style=for-the-badge" alt="LightGBM"/>
  <img src="https://img.shields.io/badge/TensorFlow-2.15+-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" alt="TensorFlow"/>
  <img src="https://img.shields.io/badge/SHAP-0.44+-8A2BE2?style=for-the-badge" alt="SHAP"/>
</p>

| Área | Tecnologías |
|---|---|
| **Lenguaje** | Python 3.10+ |
| **Datos** | pandas, NumPy |
| **ML clásico** | scikit-learn, XGBoost, LightGBM |
| **Deep Learning** | TensorFlow, Keras |
| **Interpretabilidad** | SHAP |
| **Visualización** | Matplotlib, Seaborn |

---

## 📸 Visualizaciones destacadas

### Distribución del target

![Target distribution](outputs/charts/target_distribution.png)

### Curvas ROC

![ROC curves](outputs/charts/roc_curves_final.png)

### Matrices de confusión

![Matrices de confusión](outputs/charts/matrices_confusion.png)

### Feature importance comparada

![Feature importance comparada](outputs/charts/feature_importance_comparada.png)

### SHAP Summary

![SHAP summary](outputs/charts/shap_summary.png)

### Curvas de entrenamiento (Deep Learning)

![Training curves](outputs/charts/training_curves.png)

---

## 📦 Entregables

| # | Entregable | Ubicación |
|---|---|---|
| ✅ | **Código del proyecto** | [notebooks/](notebooks/) + [scripts/](scripts/) |
| ✅ | **Informe del análisis** | [reports/informe_analisis.pdf](reports/informe_analisis.pdf) |
| ✅ | **Modelo entrenado reutilizable** | [models/trained/](models/trained/) |
| ✅ | **Presentación de resultados** | [presentation/](presentation/) |
| ✅ | **Recomendaciones de negocio** | [reports/recomendaciones.pdf](reports/recomendaciones.pdf) |
| ✅ | **Análisis de KPIs** | [reports/analisis_kpi.pdf](reports/analisis_kpi.pdf) |

---

## 🎓 Conclusiones

Este proyecto demuestra que:

1. **LightGBM supera a Deep Learning** en problemas tabulares de clasificación binaria con clases desbalanceadas.
2. **La interpretabilidad con SHAP** permite traducir el modelo en **decisiones de negocio accionables**.
3. **El 80/20 se cumple**: concentrar el esfuerzo en el 11% de clientes con mayor probabilidad captura el 80% de las conversiones potenciales.

El modelo es directamente aplicable a campañas de **venta cruzada**, con un ahorro estimado del **45% en costes de campaña**.

---

## 🔄 Próximas mejoras

- [ ] Optimización de hiperparámetros con Optuna
- [ ] Probar CatBoost como alternativa
- [ ] Despliegue del modelo como API REST (FastAPI)
- [ ] Dashboard interactivo con las predicciones
- [ ] Análisis de coste-beneficio por umbral de decisión
- [ ] Calibración de probabilidades

---

## 👤 Autora

**Judit Giravent Pineda**

- Business Analytics Student | Odisea Data
- GitHub: [@jdthgp27](https://github.com/jdthgp27)
- LinkedIn: [linkedin.com/in/judit-giravent-27b167156](https://linkedin.com/in/judit-giravent-27b167156)
- Email: jdthgp27@gmail.com

---

## 📜 Licencia

Este proyecto está bajo la **Licencia MIT**. Consulta el archivo [LICENSE](LICENSE) para más detalles.

---

*Proyecto desarrollado como parte del curso **Business Intelligence y Big Data** de Odisea Data. Septiembre 2026.*

---

⭐ Si este proyecto te ha resultado útil, considera darle una estrella en GitHub.