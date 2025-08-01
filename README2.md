
# 📊 Desafío Telecom X (parte 2)

**Autor:** Miguel Ángel Toro Romo  
**Fecha:** 8-ago-2025  

---

## 🧠 Descripción del Desafío

Este proyecto tiene como objetivo construir un modelo de clasificación que prediga si un cliente abandonará o no los servicios de la compañía, a partir de sus características sociodemográficas y de uso de servicios.

La empresa quiere anticiparse al problema de la cancelación, y debemos construir un pipeline robusto para esta etapa inicial de modelado.


---

## ✔️ Este es un problema de clasificación binaria.
     
🔷 Variable objetivo binaria (Churn = 1 o 0):

¿El cliente se irá o no?

✅ Modelos recomendados: Modelos de clasificación.

Probaremos:

*   DecisionTreeClassifier
*   RandomForestClassifier

 ---

## 🧠 Objetivos del Desafío

✅ Preparar los datos para el modelado (tratamiento, codificación, normalización).


✅ Realizar análisis de correlación y selección de variables.


✅ Entrenar dos o más modelos de clasificación.


✅ Evaluar el rendimiento de los modelos con métricas.


✅ Interpretar los resultados, incluyendo la importancia de las variables.


✅ Crear una conclusión estratégica señalando los principales factores que influyen en la cancelación.

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
├── docs/           # Documentación
│   ├── figures/    # Gráficos para documentos
│   └── report.md
└── README.md      
```

---

## ⚙️ Tecnologías Utilizadas

- <img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white"> Python 3.11.13 - Lenguaje principal
- pandas, numpy - Manipulación de datos
- scikit-learn - Machine Learning
- imbalanced-learn - Machine Learning
- matplotlib, seaborn - Visualización
- Google Colab - Entorno de ejecución

---

## 🧪 Evaluación de Modelos

Modelos evaluados:

- `RandomForestClassifier`
- `DecisionTreeClassifier`

Se construyó un pipeline completo para cada modelo que incluyen:

- Eliminación de columnas irrelevantes (`customerID`, `tenure`)
- Codificación categórica con `OneHotEncoder` para RandomForestClassifier y `SMOTE` para DecisionTreeClassifier
- Balanceo de clases con `class_weight='balanced'`
- Validación cruzada (`StratifiedKFold`)



## 🧪 Modelo Seleccionado RandomForestClassifier

En función de las métricas obtenidas en los entrenamientos de los modelos, se elige el modelo RandomForestClassifier como más eficiente

---


### 📈 Importancia de Variables

![Importancia de variables](https://drive.google.com/uc?export=view&id=ID_DE_LA_IMAGEN_IMPORTANCIA)

---

### 📊 Matriz de Confusión

![Matriz de confusión](https://drive.google.com/uc?export=view&id=ID_DE_LA_IMAGEN_MATRIZ)

---

### 🔢 Métricas

| Modelo                 | Precisión | Recall | F1-Score |
|------------------------|-----------|--------|----------|
| Random Forest          | 0.78      | 0.70   | 0.74     |
| Decision Tree          | 0.74      | 0.66   | 0.69     |

---

## 📦 Uso del Modelo Exportado

1. Cargar el modelo con `pickle`
2. Asegurarse de que los datos tengan la estructura original esperada
3. Usar `predict()` sobre el dataframe

```python
import pickle
import pandas as pd

with open("models/modelo_randomforest.pkl", "rb") as f:
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

- Las columnas `Charges.Total` y `Charges.Monthly` fueron evaluadas, y se incluye/excluye según su impacto.
- El modelo fue entrenado en un pipeline que realiza todo el preprocesamiento internamente.
- No es necesario transformar numéricamente las columnas `Yes` / `No`, ya que el pipeline lo hace automáticamente.

---

## 📷 Créditos de Imágenes

Las imágenes de métricas y gráficos se encuentran en Google Drive y se insertan usando el enlace con formato:

```
https://drive.google.com/uc?export=view&id=ID_DE_LA_IMAGEN
```

---

## 📫 Contacto

Para consultas o colaboración: [tu.email@ejemplo.com](mailto:tu.email@ejemplo.com)
