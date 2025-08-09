
# 🎯 Desafío Telecom X (parte 2)

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=1l5Ux2MaZCnJ7gHQSGb_vhqE_KR66PGio" 
       alt="Imagen de portada" 
       width="600" />
</p>

**Autor:** Miguel Ángel Toro Romo  
**Fecha:** 8-ago-2025  

---

## 📝 Descripción del Desafío

Este proyecto tiene como objetivo construir un modelo de clasificación que prediga si un cliente abandonará o no los servicios de la compañía, a partir de sus características sociodemográficas y de uso de servicios.

La empresa quiere anticiparse al problema de la cancelación, y debemos construir un pipeline robusto para esta etapa inicial de modelado.


---


### 🔍 Análisis de Problema.

🔷 Este es un problema de **clasificación binaria**.

🔷 Variable objetivo binaria (Churn = 1 o 0): ¿El cliente se irá o no?

🔷 Modelos recomendados: **Modelos de clasificación**.

🔷 Probaremos:

 *   DecisionTreeClassifier
 *   RandomForestClassifier
 *   CatBoost

 ---

## 📝 Tareas del Desafío

✅ Preparar los datos para el modelado (tratamiento, codificación, normalización).


✅ Realizar análisis de correlación y selección de variables.


✅ Entrenar dos o más modelos de clasificación.


✅ Evaluar el rendimiento de los modelos con métricas.


✅ Interpretar los resultados, incluyendo la importancia de las variables.


✅ Crear una conclusión estratégica señalando los principales factores que influyen en la cancelación.

---



## ⚙️ Tecnologías Utilizadas

- Python 3.11.13 - Lenguaje principal
- pandas 2.2.2, numpy 2.0.2- Manipulación de datos
- scikit-learn 1.6.1 - Machine Learning
- Statsmodels 0.14.5 - Machine Learning
- ImbLearn 0.13.0 - Machine Learning
- Scipy 1.16.1 - Machine Learning
- matplotlib 3.10.0, seaborn 0.13.2 - Visualización
- Google Colab - Entorno de ejecución

---

## 🔍 Análisis preliminar de la información

✅ Disponemos de un conjunto de 7043 registros con información de clientes

✅ Cada registro tiene las siguientes columnas:
```
'customerID',
'Churn',
'gender',
'SeniorCitizen',
'Partner',
'Dependents',
'tenure',
'PhoneService',
'MultipleLines',
'InternetService',
'OnlineSecurity',
'OnlineBackup',
'DeviceProtection',
'TechSupport',
'StreamingTV',
'StreamingMovies',
'Contract',
'PaperlessBilling',
'PaymentMethod',
'Charges.Monthly',
'Charges.Total'
```
### ✅ Estos registros tienen la siguiente distribución de Churn:

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=1zibE0FeRSsXAllv2Q1LaKqPiueGni8z_" 
       alt="Distribución de Churn" 
       width="700" />
</p>


### ✅ Es un conjunto de datos muy desbalanceado en sus categorías de la variable objetivo Churn


### 📈 Variables Categóricas iniciales

- `gender: 'Female', 'Male'`
- `Partner: 'Yes', 'No'`
- `Dependents: 'Yes', 'No'`
- `PhoneService: 'Yes', 'No'`
- `MultipleLines: 'No', 'Yes', 'No phone service'`
- `InternetService: 'DSL', 'Fiber optic', 'No'`
- `OnlineSecurity: 'No', 'Yes', 'No internet service'`
- `OnlineBackup: 'Yes', 'No', 'No internet service'`
- `DeviceProtection: 'No', 'Yes', 'No internet service'`
- `TechSupport: 'Yes', 'No', 'No internet service'`
- `StreamingTV: 'Yes', 'No', 'No internet service'`
- `Streaming Movies: 'No', 'Yes', 'No internet service'`
- `Contract: 'One year' 'Month-to-month', 'Two year'`
- `PaperlessBilling: 'Yes', 'No'`
- `PaymentMethod: 'Mailed check', 'Electronic check', 'Credit card (automatic)',  'Bank transfer (automatic)'`

### 📈 Variables Numéricas iniciales

- `Charges.Monthly: valores decimales mayores que cero`
- `Charges.Total: valores decimales mayores que cero'`
---

## 🧪 Evaluación de Modelos

🔷 Modelos evaluados:

 - `RandomForestClassifier`
 - `DecisionTreeClassifier`
 - `CatBoost`

🔷 Se construyó un pipeline completo para cada modelo que incluyen:

 - Eliminación de columnas irrelevantes (`customerID`, `tenure`)
 - Codificación categórica con `OneHotEncoder` 
- Balanceo de clases con `class_weight='balanced` para `RandomForestClassifier` y `SMOTE` para `DecisionTreeClassifier`
- Validación cruzada (`StratifiedKFold`)

---

### 🔢 Métricas

🔷 DecisionTreeClassifier con datos balanceados con `SMOTE`.

```
              precision    recall  f1-score   support

           0       0.86      0.79      0.83      1035
           1       0.53      0.66      0.59       374

    accuracy                           0.76      1409
   macro avg       0.70      0.72      0.71      1409
weighted avg       0.78      0.76      0.76      1409

```


🔷RandomForestClassifier con `class_weight='balanced`.
```
              precision    recall  f1-score   support

          No       0.91      0.67      0.77      1035
         Yes       0.47      0.81      0.60       374

    accuracy                           0.71      1409
   macro avg       0.69      0.74      0.69      1409
weighted avg       0.79      0.71      0.73      1409

```
---

## ✔️ Modelo Seleccionado

### **`RandomForestClassifier`**
- En función de las métricas obtenidas en los entrenamientos de los modelos, se elige este modelo como el más eficiente para la clasificación de la clase 1 (clientes que abandonan).
- Mejores parámetros RandomForest:
  -   'max_depth': 5
  -   'min_samples_leaf': 3
  -   'min_samples_split': 2
  -   'n_estimators': 100

---



### 📈 Importancia de Variables codificadas

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=1E7Fv6JqBvJcV2-i07TrgM6vHe3GSbMx2" 
       alt="Importancia de variables" 
       width="600" />
</p>

---

### 📊 Matriz de Confusión

<p align="center">
 <img src="https://drive.google.com/uc?export=view&id=1KwCMW0Rj9pS1-tPO-7vvLyBlUaUEq00M" 
       alt="Matriz de Confusión" 
       width="600" />
</p>

---

### 📊 Curva ROC

<p align="center">
 <img src="https://drive.google.com/uc?export=view&id=1Nhcch6II5I9xTgzKj5ETRBljYeA-R5Ss" 
       alt="Curva ROC" 
       width="450" />
</p>

---

## 📦 Uso del Modelo Exportado

1. Cargar el modelo con `pickle`
2. Asegurarse de que los datos tengan la estructura original esperada
3. Usar `predict()` sobre el dataframe

```python
import pickle
import pandas as pd

with open("models/modelo_randomforest_pipeline.pkl", "rb") as f:
    modelo = pickle.load(f)

nuevos_datos = pd.read_csv("data/nuevos_clientes.csv")
resultado = modelo.predict(nuevos_datos)
```

---

## 🚀 Ejecución Rápida

Puedes ejecutar el flujo completo con el script:

```bash
python scripts/predict_from_csv.py --input data/nuevos_clientes.csv
```

---

## 📝 Notas

- Las columnas `Charges.Total` y `Charges.Monthly` fueron evaluadas, y se incluyeron porque daban mejor resultado que al excluirlas.
- El modelo fue entrenado en un pipeline que realiza todo el preprocesamiento internamente.
- No es necesario transformar numéricamente las columnas `Yes` / `No`, ya que el pipeline lo hace automáticamente.
- En datos nuevos se deben ingresar con tenure=0, Charges.Total = 0 y Charges.Monthly = 0

---

## 📷 Créditos de Imágenes

Las imágenes de métricas y gráficos se encuentran en Google Drive y se insertan usando el enlace con formato:

```
https://drive.google.com/uc?export=view&id=ID_DE_LA_IMAGEN
```

---
## 📂 Estructura del Repositorio

```
Telecom_X_part_2
├── data/           # Datos crudos
├── notebooks/      # Colab
├── src/            # Código fuente
├── output/         # Gráficos generados por scripts
│   ├── exploratory/
│   └── results/
├── models/         # modelos generados
├── docs/           # Documentación
│   ├── figures/    # Gráficos para documentos
│   └── report.md
└── README.md      
```

---
## 📫 Contacto

Para consultas o colaboración: [miguel.toro.romo@gmail.com](mailto:miguel.toro.romo@gmail.com)
