
# 📊 Proyecto de Predicción de Abandono de Clientes (Churn)

**Autor:** [Tu Nombre o Usuario de GitHub]  
**Fecha:** [Fecha del proyecto]  

---

## 🧠 Descripción del Proyecto

Este proyecto tiene como objetivo construir un modelo de clasificación que prediga si un cliente abandonará o no los servicios de la compañía, a partir de sus características sociodemográficas y de uso de servicios.

---

## 📂 Estructura del Repositorio

```
├── notebooks/          # Cuadernos Jupyter de desarrollo y validación
├── data/               # Datos crudos y preprocesados
├── models/             # Modelos entrenados (Pickle)
├── scripts/            # Scripts reutilizables
├── README.md           # Este archivo
```

---

## ⚙️ Tecnologías Utilizadas

- Python 3.10
- pandas, numpy
- scikit-learn
- imbalanced-learn
- matplotlib, seaborn
- Jupyter Notebook

---

## 🧪 Evaluación del Modelo

Se construyó un pipeline completo que incluye:

- Eliminación de columnas irrelevantes (`customerID`, `Charges.Total`, etc.)
- Codificación categórica con `OneHotEncoder`
- Balanceo de clases con `class_weight='balanced'`
- Validación cruzada (`StratifiedKFold`)

Modelos evaluados:

- `RandomForestClassifier`
- `DecisionTreeClassifier`

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
