Predicción de Venta Cruzada en Seguros de Salud
Curso: Business Intelligence y Big Data (Nivel 5) | Odisea Data
Reto: Implementación de algoritmos avanzados de IA en Business Analytics
Dataset: Health Insurance Cross Sell Prediction (Kaggle)
Entorno: Google Colab + Python 3.10+

📌 Descripción del Proyecto
Una compañía de seguros de salud desea optimizar su estrategia de venta cruzada ofreciendo seguros de vehículo a sus clientes actuales. El objetivo de este proyecto es construir un modelo predictivo de clasificación binaria que identifique qué asegurados tienen mayor probabilidad de estar interesados en adquirir una póliza de automóvil.

Este tipo de modelo permite a la empresa:

Dirigir sus campañas de marketing únicamente a los clientes con mayor propensión a la compra.

Reducir costes de comunicación y mejorar el retorno de la inversión (ROI).

Optimizar su modelo de negocio y aumentar los ingresos por venta cruzada.

El dataset contiene 381.109 registros de clientes con seguros de salud, con 12 variables que incluyen datos demográficos, información sobre el vehículo, historial de seguros y el canal de contacto.

🎯 Objetivos del Proyecto
Explorar y comprender el dataset: estructura, variables clave, análisis descriptivo y detección de desbalanceo de clases.

Preparar y limpiar los datos: tratamiento de valores nulos, atípicos, codificación de variables categóricas y escalado.

Desarrollar modelos avanzados de IA: Random Forest, Gradient Boosting (XGBoost/LightGBM) y redes neuronales profundas.

Evaluar y comparar los modelos con métricas robustas para datos desbalanceados: F1-score, Recall y AUC-ROC.

Extraer insights de negocio e interpretar los resultados con técnicas como SHAP y LIME para entender qué factores influyen en la decisión del cliente.

Generar recomendaciones prácticas para la toma de decisiones en la estrategia de venta cruzada.

📊 Estructura del Dataset
Variable	Descripción
id	Identificador único del cliente
Gender	Género del cliente
Age	Edad del cliente
Driving_License	0: No tiene carné, 1: Tiene carné
Region_Code	Código de la región del cliente
Previously_Insured	1: Ya tiene seguro de vehículo, 0: No tiene
Vehicle_Age	Antigüedad del vehículo
Vehicle_Damage	1: Ha sufrido daños, 0: No ha sufrido daños
Annual_Premium	Prima anual que paga el cliente
PolicySalesChannel	Canal de contacto (anónimo)
Vintage	Días de antigüedad del cliente en la compañía
Response	Variable objetivo: 1: Interesado, 0: No interesado
🛠️ Stack Tecnológico
Lenguaje: Python 3.10+

Manipulación de datos: Pandas, NumPy

Visualización: Matplotlib, Seaborn

Machine Learning: Scikit-learn, XGBoost, LightGBM

Deep Learning: TensorFlow / Keras

Interpretabilidad: SHAP, LIME

Entorno: Google Colab

📁 Estructura del Proyecto
text
reto2-ia-business-analytics/
├── data/                  # Datasets (raw, processed, external)
├── notebooks/             # Jupyter Notebooks por fase
├── scripts/               # Código reutilizable (preprocess, train, evaluate)
├── models/                # Modelos entrenados y scalers
├── outputs/               # Gráficos, métricas y capturas de pantalla
├── reports/               # Informes en Markdown
└── presentation/          # Presentación final de resultados
📈 Resultados Esperados
Modelo con mejor rendimiento: XGBoost o Random Forest, con un AUC-ROC superior a 0.85 y un F1-score en torno al 0.45, valores típicos en este dataset debido al fuerte desbalanceo de clases.

Variables más influyentes: Previously_Insured, Vehicle_Damage y Age son los predictores más importantes según la literatura.

Recomendaciones de negocio: Estrategias de contacto segmentadas por perfil de cliente y canal óptimo.

📦 Entregables
□ Código del proyecto → scripts/ + notebooks/
□ Informe del análisis → reports/informe_analisis.md
□ Modelo entrenado reutilizable → models/trained/
□ Presentación de resultados → presentation/
👤 Autor
Judit Giravent
Business Analytics Student | Odisea Data