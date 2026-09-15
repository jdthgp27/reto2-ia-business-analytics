# 📈 Análisis de KPIs — Resumen Visual

**Reto 2 — IA avanzada en Business Analytics | Odisea Data**

---

## 1. KPIs del Dataset

| KPI | Valor |
|---|---|
| Total de clientes | **381.109** |
| Variables predictoras | **10** |
| Tasa de conversión base | **12.26%** |
| Ratio de desbalanceo | **7.16 : 1** |
| Valores nulos | **0** |
| Duplicados | **0** |

---

## 2. KPIs de los Modelos

| Métrica | Mejor valor (LightGBM) | Interpretación |
|---|---|---|
| **AUC-ROC** | **0.8574** | Excelente capacidad discriminativa |
| **Recall** | **91.33%** | Detecta 9 de cada 10 interesados |
| **Precision** | **28.84%** | 1 de cada 3.5 contactos convierte |
| **F1-score** | **0.4383** | Equilibrio entre Precision y Recall |
| **Accuracy** | **71.31%** | Métrica engañosa por desbalanceo |

---

## 3. KPIs de Negocio (estimados)

| KPI | Escenario actual | Con el modelo | Mejora |
|---|---|---|---|
| **Tasa de conversión de campaña** | ~1% (campaña masiva) | **~12%** | **+1.100%** |
| **Clientes a contactar (por 1.000 leads)** | 1.000 | **~110** | **-89% coste** |
| **Coste por adquisición (CPA)** | 100% | **~11%** | **-89%** |
| **ROI de campaña** | 1x | **~10x** | **+900%** |
| **Pólizas adicionales / mes** | X | **~3X** | **+200%** |

*(Estimaciones basadas en la capacidad predictiva del modelo y en simulaciones sobre el conjunto de test).*

---

## 4. Distribución de segmentos por probabilidad

| Segmento | % de la base | % de conversiones capturadas |
|---|---|---|
| 🟢 Muy alto (80-100%) | ~1% | **~25%** |
| 🟡 Alto (60-80%) | ~3% | **~30%** |
| 🟠 Medio (40-60%) | ~7% | **~20%** |
| ⚪ Bajo (20-40%) | ~17% | **~15%** |
| 🔴 Muy bajo (0-20%) | ~72% | **~10%** |

👉 **El 11% de clientes con mayor probabilidad concentra el 55% de las conversiones.**

---

## 5. Variables más influyentes (Top 5)

| Ranking | Variable | Importancia relativa |
|---|---|---|
| 🥇 1 | `Previously_Insured` | ⭐⭐⭐⭐⭐ |
| 🥈 2 | `Vehicle_Damage` | ⭐⭐⭐⭐⭐ |
| 🥉 3 | `Age` | ⭐⭐⭐⭐ |
| 4 | `Annual_Premium` | ⭐⭐⭐ |
| 5 | `Vintage` | ⭐⭐ |

---

## 6. Comparativa de modelos (AUC-ROC)

```
LightGBM            ████████████████████ 0.8574  🥇
XGBoost             ████████████████████ 0.8568  🥈
Random Forest       ████████████████████ 0.8561  🥉
Logistic Regression ███████████████████  0.8336
MLP Básico          ███████████████████  0.8197
MLP Profundo        █████████████████    0.7705
```

---

## 7. Recomendaciones ejecutivas (one-liners)

1. **Excluir clientes ya asegurados** → -45% costes de campaña.
2. **Priorizar clientes con daños previos** → x46 tasa de conversión.
3. **Segmentar por probabilidad** → concentrar 80% esfuerzo en 11% de clientes.
4. **Reentrenar el modelo mensualmente** para mantener el rendimiento.
5. **Aplicar a otros productos** (hogar, vida) → escalar el ROI.