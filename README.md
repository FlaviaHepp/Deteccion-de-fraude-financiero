# 🛡️ Detección de Fraude Financiero con Machine Learning

## 📌Descripción del proyecto

Este proyecto implementa un sistema de detección de fraude financiero utilizando datos transaccionales reales a gran escala (más de 6 millones de registros).
El objetivo es identificar transacciones fraudulentas mediante técnicas de análisis exploratorio de datos (EDA), ingeniería de características, preprocesamiento avanzado y modelos de clasificación supervisada, abordando explícitamente el desbalance severo de clases, típico en problemas de fraude.

El trabajo compara múltiples algoritmos de Machine Learning y evalúa su desempeño utilizando métricas apropiadas para entornos financieros.

## 🎯Objetivos del proyecto

- Analizar patrones y comportamientos asociados a transacciones fraudulentas.
- Tratar correctamente el desbalance de clases.
- Evaluar distintos enfoques de preprocesamiento y escalado.
- Comparar modelos clásicos y avanzados de clasificación.
- Optimizar la detección de fraude minimizando falsos negativos.
- Evaluar modelos con métricas robustas (ROC-AUC, Balanced Accuracy).

## 🏦Contexto del problema

La detección de fraude es un problema crítico en banca y fintech, donde:
- El fraude representa un porcentaje muy pequeño del total de transacciones.
- Un falso negativo implica pérdidas económicas directas.
- Un falso positivo impacta en la experiencia del cliente.

📌 Por ello, accuracy tradicional no es suficiente y se priorizan métricas como:
- ROC-AUC
- Balanced Accuracy
- Matriz de confusión

## 📊 Dataset

- Tipo: Datos transaccionales financieros
- Tamaño: +6 millones de registros
- Variable objetivo: isFraud (0 = legítima, 1 = fraudulenta)

Principales variables:
- step: unidad temporal de la transacción
- type: tipo de transacción (transfer, payment, etc.)
- amount: monto de la transacción
- oldbalanceOrg, newbalanceOrig: saldos de la cuenta origen
- oldbalanceDest, newbalanceDest: saldos de la cuenta destino
- isFlaggedFraud: indicador de fraude marcado por reglas

📌 Se eliminan identificadores (nameOrig, nameDest) para evitar leakage.

## 🔍Metodología

1️⃣ Análisis Exploratorio de Datos (EDA)
- Inspección de estructura y calidad de datos.
- Análisis de distribución de clases (fraude vs no fraude).
- Visualización de montos en escala logarítmica.
- Análisis por tipo de transacción.
- Matriz de correlaciones entre variables numéricas.

2️⃣ Preprocesamiento
- Separación de variables numéricas y categóricas.
- Codificación One-Hot (type).
- Evaluación comparativa de escaladores:
- StandardScaler
- MinMaxScaler
- RobustScaler
- PowerTransformer

Selección del mejor escalado según desempeño del modelo base.

3️⃣ Modelado

📌 Clasificador base
- Logistic Regression con class_weight='balanced'
- Comparación de escaladores usando Balanced Accuracy

👉El PowerTransformer resulta el mejor preprocesamiento para el modelo base.

📌Modelos evaluados
- Decision Tree
- HistGradientBoosting
- XGBoost
- LightGBM
- CatBoost
- KNN
- Random Forest

📌Los modelos se entrenan considerando:
- Pesos de clase
- Desbalance extremo
- Escenarios realistas de fraude

4️⃣ Evaluación

Métricas utilizadas:
- Balanced Accuracy
- ROC-AUC
- Classification Report
- Matriz de confusión
- Curvas ROC comparativas

📌Se prioriza la capacidad del modelo para detectar fraude sin depender del accuracy tradicional.

## 📈Resultados principales

- CatBoost y Random Forest presentan el mejor desempeño global.
- Random Forest alcanza un ROC-AUC cercano a 1.0, mostrando alta capacidad discriminatoria.
- Los montos de transacciones fraudulentas presentan distribuciones distintas a las legítimas.
- El tipo de transacción es una variable altamente informativa.
- El uso de métricas balanceadas es clave para una evaluación realista.

## 🛠️Tecnologías y Librerías

- Python
- Pandas / NumPy
- Matplotlib / Seaborn
- Scikit-learn
- XGBoost
- LightGBM
- CatBoost
- TQDM
- Skimpy

## 📁Estructura del proyecto

├── Transactions Data.csv
├── Detección de fraude financiero.py
└── README.md


## 🚀Posibles mejoras futuras

- Ajuste de hiperparámetros (Grid / Bayesian Search).
- Técnicas de resampling (SMOTE, NearMiss).
- Umbrales de decisión optimizados por costo.
- Interpretabilidad con SHAP.
- Pipeline completo para producción.
- Simulación de fraude en tiempo real.

## 👤Autora

Flavia Hepp
Proyecto de Data Science aplicado a detección de fraude, banca y fintech.
