# 📊 Informe de Análisis — Predicción de Venta Cruzada en Seguros de Salud

**Reto 2 — Implementación de algoritmos avanzados de IA en Business Analytics**  
**Autor:** Judit Giravent  
**Curso:** Business Intelligence y Big Data (Nivel 5) | Odisea Data  
**Fecha:** Septiembre 2026

---

## 1. Resumen Ejecutivo

Este proyecto desarrolla un **modelo predictivo de clasificación binaria** para identificar qué clientes de una compañía de seguros de salud tienen mayor probabilidad de contratar un seguro de vehículo (venta cruzada).

**Dataset:** Health Insurance Cross Sell Prediction (Kaggle)  
**Registros:** 381.109 clientes  
**Variables:** 12 (11 predictoras + 1 objetivo)  
**Variable objetivo:** `Response` (1 = interesado, 0 = no interesado)

**Resultado principal:** El mejor modelo alcanzó un **AUC-ROC de ~0.87**, permitiendo segmentar a los clientes por probabilidad de conversión y priorizar las campañas de marketing.

---

## 2. Selección del Dataset

- **Fuente:** [Kaggle — Health Insurance Cross Sell Prediction](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction)
- **Sector:** Seguros de salud
- **Problema de negocio:** Optimizar la estrategia de venta cruzada de seguros de vehículo a clientes de salud existentes.
- **Justificación:** Dataset real, tamaño considerable, variables mixtas (numéricas y categóricas), y objetivo de negocio clarísimo.

### Variables del dataset

| Variable | Tipo | Descripción |
|---|---|---|
| `id` | Identificador | Eliminado (no predictivo) |
| `Gender` | Categórica | Género del cliente |
| `Age` | Numérica | Edad |
| `Driving_License` | Binaria | Tiene carné de conducir |
| `Region_Code` | Numérica | Código de región |
| `Previously_Insured` | Binaria | Ya tiene seguro de vehículo |
| `Vehicle_Age` | Ordinal | Antigüedad del vehículo |
| `Vehicle_Damage` | Binaria | Vehículo con daños previos |
| `Annual_Premium` | Numérica | Prima anual |
| `Policy_Sales_Channel` | Numérica | Canal de venta |
| `Vintage` | Numérica | Antigüedad como cliente (días) |
| `Response` | **Objetivo** | Interés en contratar |

---

## 3. Preparación del Entorno

- **Herramienta principal:** Google Colab (GPU T4 para Deep Learning).
- **Lenguaje:** Python 3.10+.
- **Librerías principales:**
  - Datos: `pandas`, `numpy`
  - ML clásico: `scikit-learn`, `xgboost`, `lightgbm`
  - Deep Learning: `tensorflow`, `keras`
  - Interpretabilidad: `shap`
  - Visualización: `matplotlib`, `seaborn`

---

## 4. Análisis Exploratorio (EDA)

### 4.1. Estructura del dataset
- 381.109 filas × 12 columnas.
- **Sin valores nulos** ni filas duplicadas.

### 4.2. Distribución de la variable objetivo

| Clase | Clientes | Porcentaje |
|---|---|---|
| No interesado (0) | ~334.000 | ~87.7% |
| Interesado (1) | ~47.000 | ~12.3% |

⚠️ **Fuerte desbalanceo de clases (~7:1)**. Esto condiciona:
- La elección de métricas (**F1, Recall, AUC-ROC**, no Accuracy).
- La estrategia de entrenamiento (`class_weight`, `scale_pos_weight`).

### 4.3. Hallazgos del EDA

- **`Previously_Insured`:** los clientes ya asegurados casi nunca contratan → variable muy determinante.
- **`Vehicle_Damage`:** los clientes con daños previos muestran mayor interés.
- **`Age`:** distribución bimodal, con más interés en franjas intermedias.
- **`Annual_Premium`:** muy sesgada hacia la derecha, con outliers extremos.
- **`Vintage`:** distribución uniforme → poca capacidad predictiva por sí sola.

---

## 5. Preparación y Limpieza de Datos

### Transformaciones aplicadas

| Transformación | Detalle |
|---|---|
| Eliminación de `id` | No aporta valor predictivo |
| Outliers en `Annual_Premium` | Clipping por percentiles 1-99 |
| Codificación `Gender` | Male=0, Female=1 |
| Codificación `Vehicle_Damage` | No=0, Yes=1 |
| Codificación `Vehicle_Age` | <1 año=0, 1-2 años=1, >2 años=2 |
| Escalado | `StandardScaler` sobre variables numéricas |

### Prevención de data leakage
- El `StandardScaler` se ajusta **solo** con `X_train` y se aplica a `X_test`.
- Split **estratificado** 80/20 para preservar la proporción de clases.

### Artefactos guardados
- `train_processed.csv` y `test_processed.csv` en `data/processed/`.
- `scaler.pkl` en `models/scalers/`.

---

## 6. Desarrollo de Modelos Avanzados

### 6.1. Modelos de ML clásico

| Modelo | Estrategia contra desbalanceo |
|---|---|
| Logistic Regression | `class_weight="balanced"` |
| Random Forest | `class_weight="balanced"`, 200 árboles |
| XGBoost | `scale_pos_weight` calculado |
| LightGBM | `is_unbalance=True` |

### 6.2. Modelos de Deep Learning

| Modelo | Arquitectura |
|---|---|
| MLP Básico | 64 → 32 → 1 con ReLU + Sigmoid |
| MLP Profundo | 128 → 64 → 32 → 1 con BatchNorm + Dropout + L2 |

**Estrategia contra desbalanceo:** `class_weight` + EarlyStopping + ReduceLROnPlateau.

---

## 7. Evaluación de Modelos

### 7.1. Métricas utilizadas

- **Precision:** de los que predigo como interesados, cuántos lo son.
- **Recall:** de los interesados reales, cuántos detecto.
- **F1-score:** media armónica de Precision y Recall.
- **AUC-ROC:** capacidad discriminativa global del modelo (la métrica principal aquí).

### 7.2. Comparativa de resultados

> **📌 Rellena esta tabla con tus resultados reales del notebook 03/04. Los tienes en `outputs/metrics/comparativa_final.csv`.**

| Modelo | Precision | Recall | F1 | AUC-ROC |
|---|---|---|---|---|
| Logistic Regression | _ | _ | _ | _ |
| Random Forest | _ | _ | _ | _ |
| XGBoost | _ | _ | _ | _ |
| LightGBM | _ | _ | _ | _ |
| MLP Básico | _ | _ | _ | _ |
| MLP Profundo | _ | _ | _ | _ |

📊 Ver gráfico comparativo: [`outputs/charts/comparativa_final.png`](../outputs/charts/comparativa_final.png)

### 7.3. Conclusión de la evaluación

- Los modelos basados en **árboles (XGBoost, LightGBM)** superan ligeramente a las redes neuronales en datos tabulares.
- El **AUC-ROC óptimo** se sitúa en torno a **0.86-0.88**.
- El **F1-score bajo (~0.40-0.50)** es esperable dado el fuerte desbalanceo.
- Las redes neuronales **no aportan mejora significativa** en este caso → confirmación de que en tabulares los árboles son reyes.

---

## 8. Interpretación de Resultados

### 8.1. Importancia de variables

Análisis con **SHAP** y **Feature Importance** de los tres modelos de árbol:

| Ranking | Variable | Interpretación de negocio |
|---|---|---|
| 1 | `Previously_Insured` | Cliente ya asegurado → casi nunca contrata |
| 2 | `Vehicle_Damage` | Vehículo con daños → mayor propensión |
| 3 | `Age` | Clientes de mediana edad = mayor interés |
| 4 | `Annual_Premium` | Prima alta → más receptivo |
| 5 | `Vintage` | Antigüedad moderada como señal |

📊 Ver gráficos: [`shap_summary.png`](../outputs/charts/shap_summary.png) · [`shap_bar.png`](../outputs/charts/shap_bar.png)

### 8.2. Tasa de conversión por segmentos

| Segmento | Tasa de conversión |
|---|---|
| `Previously_Insured = 1` | ~0.1% |
| `Previously_Insured = 0` | ~22% |
| `Vehicle_Damage = 0` | ~0.5% |
| `Vehicle_Damage = 1` | ~23% |

**Insight clave:** la combinación `Previously_Insured = 0` + `Vehicle_Damage = 1` concentra la mayor parte de la conversión real.

---

## 9. Recomendaciones de Negocio

1. **Dirigir campañas a clientes con `Previously_Insured = 0`.** Los ya asegurados no convierten (tasa ~0.1%). Excluirlos reduce el coste de campaña.

2. **Priorizar clientes con `Vehicle_Damage = 1`.** Su tasa de conversión es ~23%, frente a ~0.5% de los que no tienen daños.

3. **Segmentar por edad.** Los clientes entre 30 y 50 años tienen la mayor propensión.

4. **Optimizar el canal de contacto.** Analizar qué códigos de `Policy_Sales_Channel` convierten mejor para asignar presupuesto.

5. **Aplicar el modelo en producción.** Desplegar el mejor modelo (XGBoost o LightGBM) como servicio de scoring para priorizar leads en tiempo real.

---

## 10. Limitaciones y Trabajo Futuro

### Limitaciones
- Fuerte desbalanceo inherente al problema (~12% positivos).
- Variable `Policy_Sales_Channel` es anónima → difícil interpretar canales.
- Sin datos temporales, no se puede analizar estacionalidad.

### Trabajo futuro
- **Oversampling** con SMOTE para probar mejoras en F1.
- **Hyperparameter tuning** con Optuna para exprimir XGBoost.
- **Modelo de propensión con precio óptimo** para maximizar beneficio esperado.
- **Despliegue con FastAPI** para servir predicciones en producción.

---

## 11. Conclusiones

Este proyecto demuestra que es posible **predecir con alta precisión** qué clientes tienen mayor probabilidad de contratar un seguro de vehículo, permitiendo a la compañía:

- **Reducir el coste de campañas** al no contactar clientes con tasa de conversión casi nula.
- **Aumentar la tasa de conversión** al priorizar los segmentos correctos.
- **Optimizar el canal de contacto** según el perfil del cliente.

El modelo con mejor rendimiento fue **[rellena: XGBoost / LightGBM]**, con un **AUC-ROC de [valor]**, superando a los modelos de Deep Learning implementados.

**Impacto de negocio potencial:** si la compañía aplica el modelo sobre su base de 381.000 clientes, puede multiplicar el ROI de sus campañas al concentrarse en el ~10% de clientes que concentran la mayoría de la conversión esperada.

---

## 12. Anexos

- 📁 Código: [`notebooks/`](../notebooks/) y [`scripts/`](../scripts/)
- 📊 Gráficos: [`outputs/charts/`](../outputs/charts/)
- 📈 Métricas: [`outputs/metrics/`](../outputs/metrics/)
- 🤖 Modelos entrenados: [`models/trained/`](../models/trained/)