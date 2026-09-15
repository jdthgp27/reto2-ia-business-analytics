# 💼 Recomendaciones de Negocio — Venta Cruzada de Seguros de Vehículo

**Reto 2 — IA avanzada en Business Analytics | Odisea Data**  
**Autor:** Judit Giravent  
**Audiencia:** Dirección Comercial y Marketing

---

## 1. Contexto

Una compañía de seguros de salud dispone de **381.109 clientes** y quiere venderles un **seguro de vehículo** (venta cruzada). El reto: **contactar solo a los clientes con mayor probabilidad de compra** para no malgastar presupuesto.

**Solución propuesta:** un modelo de IA (LightGBM) que asigna a cada cliente una **probabilidad de compra** entre 0 y 1, con una capacidad predictiva del **85.7%** (AUC-ROC).

---

## 2. Hallazgo principal — El "cliente ideal"

El análisis revela un patrón clarísimo. El cliente con **mayor probabilidad de compra** cumple 3 condiciones:

| Condición | Valor ideal |
|---|---|
| 🚗 **Vehículo con daños previos** | `Vehicle_Damage = 1` |
| 📋 **No tiene seguro de vehículo actualmente** | `Previously_Insured = 0` |
| 👤 **Edad intermedia** | Entre 30 y 50 años |

**Tasa de conversión de este perfil: ~23%**  
**Tasa de conversión del resto: ~1%**

👉 **Concentrar los esfuerzos en este segmento multiplica la eficiencia de las campañas por 20.**

---

## 3. Recomendaciones accionables

### 🎯 Recomendación 1 — Excluir clientes ya asegurados

**Acción:** eliminar de todas las campañas a los clientes con `Previously_Insured = 1`.

**Justificación:**
- Su tasa de conversión es **~0.1%** (1 de cada 1.000).
- Representan más del **45% de la base de clientes**.
- Contactarles genera coste sin retorno.

**Impacto esperado:**
- Reducción del **~45%** en costes de contacto.
- Aumento del **ROI de campaña** por concentración en el público objetivo.

---

### 🎯 Recomendación 2 — Priorizar clientes con daños previos en el vehículo

**Acción:** crear una **campaña específica** para clientes con `Vehicle_Damage = 1`.

**Justificación:**
- Su tasa de conversión es **~23%** frente al **~0.5%** de los clientes sin daños.
- Este perfil suele estar predispuesto a renovar o complementar su protección.

**Impacto esperado:**
- Multiplicar por **~46** la tasa de conversión frente al segmento sin daños.
- Justifica una **inversión publicitaria más agresiva** en este segmento.

---

### 🎯 Recomendación 3 — Segmentar las campañas por probabilidad predicha

**Acción:** usar el modelo para clasificar a cada cliente en 5 segmentos y aplicar **una estrategia distinta por segmento**.

| Segmento | Probabilidad | % de la base | Acción recomendada | Canal |
|---|---|---|---|---|
| 🟢 **Muy alto** | 80-100% | ~1% | Contacto personalizado (llamada + email) | Agente comercial |
| 🟡 **Alto** | 60-80% | ~3% | Email personalizado + llamada de seguimiento | Email + teléfono |
| 🟠 **Medio** | 40-60% | ~7% | Email marketing con contenido educativo | Email |
| ⚪ **Bajo** | 20-40% | ~17% | Email masivo con bajo coste | Email automatizado |
| 🔴 **Muy bajo** | 0-20% | ~72% | **No contactar** | — |

**Impacto esperado:**
- Concentrar el **80% del esfuerzo comercial** en el **11% de clientes** con mayor probabilidad.
- Ahorro estimado: **~70% del presupuesto de contacto** actual.

---

### 🎯 Recomendación 4 — Optimizar el canal de venta

**Acción:** analizar qué códigos de `Policy_Sales_Channel` tienen mejor tasa de conversión y **reasignar presupuesto** hacia los más efectivos.

**Justificación:**
- No todos los canales convierten igual. Algunos canales muestran tasas muy superiores al promedio.
- El modelo aprende automáticamente qué canales son más predictivos.

**Impacto esperado:**
- Mejora del **coste por adquisición (CPA)** al concentrar inversión en canales efectivos.

---

### 🎯 Recomendación 5 — Personalizar la oferta según prima anual

**Acción:** ajustar el producto ofrecido en función de la prima anual del cliente (`Annual_Premium`).

**Justificación:**
- Los clientes con **primas más altas** muestran mayor propensión a productos complementarios.
- Ofrecer el mismo producto a todos genera fatiga y baja respuesta.

**Impacto esperado:**
- Aumento del **ticket medio** por cliente mediante ofertas mejor ajustadas a su perfil.

---

## 4. Plan de implementación sugerido

| Fase | Plazo | Acciones |
|---|---|---|
| **1. Piloto** | Mes 1 | Lanzar campaña al segmento "Muy alto" (1% de la base) y medir conversión real vs predicha. |
| **2. Validación** | Mes 2 | Comparar resultados con un grupo de control sin modelo. Calcular el ROI incremental. |
| **3. Escalado** | Mes 3-4 | Extender la campaña a los segmentos "Alto" y "Medio". Automatizar el scoring diario. |
| **4. Optimización** | Mes 5+ | Reentrenar el modelo mensualmente con los datos reales de conversión. Añadir nuevas variables. |

---

## 5. KPIs para medir el impacto

| KPI | Valor actual estimado | Objetivo tras el modelo |
|---|---|---|
| **Tasa de conversión global** | ~12% | **~18-20%** |
| **Coste por adquisición (CPA)** | 100% (baseline) | **-40%** |
| **ROI de campaña** | 100% (baseline) | **+150-200%** |
| **Clientes contactados por 1.000€** | 100% | Concentración 10x en segmentos top |
| **Pólizas adicionales / mes** | — | **+30-50%** |

*(Los valores objetivo son estimaciones basadas en la capacidad predictiva del modelo y deben validarse con el piloto).*

---

## 6. Riesgos y cómo mitigarlos

| Riesgo | Mitigación |
|---|---|
| **Falsos positivos altos** (clientes que el modelo dice que comprarán y no lo hacen) | Empezar por el segmento "Muy alto" (mayor precisión) y escalar gradualmente. |
| **Sesgo por antigüedad** (`Vintage` influye poco) | Añadir variables temporales y de comportamiento al modelo. |
| **Cambios en el mercado** (nuevos competidores, regulación) | Reentrenar el modelo mensualmente para capturar la evolución. |
| **Fatiga de campaña** en clientes recurrentes | Limitar el número de contactos por cliente y mes. |

---

## 7. Recomendación final

El modelo desarrollado ofrece un **retorno de inversión muy alto** con un coste de implementación mínimo:

- 🎯 **No requiere infraestructura compleja**: puede desplegarse como una API sencilla o incluso con hojas de cálculo en la fase piloto.
- 📊 **Permite empezar pequeño**: un piloto con solo el 1% de la base permite validar el impacto en 4-6 semanas.
- 🔄 **Es escalable**: el mismo modelo puede aplicarse a otros productos de venta cruzada (hogar, vida, etc.).

**Conclusión:** la aplicación de este modelo permite transformar una campaña masiva de bajo retorno en una **estrategia quirúrgica de alto impacto**, alineada con el objetivo de negocio de maximizar el valor del cliente (Customer Lifetime Value).

---

*Este documento forma parte del Reto 2 — Implementación de algoritmos avanzados de IA en Business Analytics del curso Business Intelligence y Big Data de Odisea Data.*