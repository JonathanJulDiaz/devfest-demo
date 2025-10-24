# 🧠 Análisis Predictivo de Riesgo Crediticio con Python y Google Colab

Este proyecto fue desarrollado como **demo educativa para Google DevFest**, con el objetivo de mostrar cómo aplicar **análisis predictivo e inteligencia artificial** usando **Python** y **Google Colab** sobre un dataset de préstamos bancarios.

---

## 📂 Contenido del repositorio

- **`credit_risk_dataset.csv`** → Dataset con información de clientes y préstamos.  
- **`credit_risk_analysis.ipynb`** → Cuaderno de Google Colab con el análisis, preprocesamiento, visualizaciones y modelo predictivo.

---

## 🎯 Objetivo del proyecto

Predecir si un solicitante de préstamo **tiene riesgo de incumplimiento (default)** utilizando datos históricos.  
El modelo aprende patrones en variables demográficas, laborales y crediticias para anticipar resultados futuros.

---

## 📊 Descripción del dataset

Cada fila representa una solicitud de préstamo. Las principales columnas son:

| Columna | Descripción |
|----------|-------------|
| `person_age` | Edad del solicitante |
| `person_income` | Ingreso anual |
| `person_home_ownership` | Tipo de vivienda (RENT, OWN, MORTGAGE, OTHER) |
| `person_emp_length` | Años de empleo |
| `loan_intent` | Propósito del préstamo |
| `loan_grade` | Calificación crediticia (A–G) |
| `loan_amnt` | Monto del préstamo |
| `loan_int_rate` | Tasa de interés aplicada |
| `loan_status` | Estado del préstamo (0 = no incumple, 1 = incumple) |
| `loan_percent_income` | Porcentaje del ingreso destinado al préstamo |
| `cb_person_default_on_file` | Historial de incumplimiento (Y/N) |
| `cb_person_cred_hist_length` | Longitud del historial crediticio (en años) |

---

## 🧹 Preprocesamiento de datos

Se realizaron las siguientes tareas antes de entrenar el modelo:

1. **Revisión de valores faltantes**  
   - Se imputaron nulos con la **mediana** (`person_emp_length`) y **media** (`loan_int_rate`).

2. **Filtrado de datos inconsistentes**  
   - Se eliminaron filas donde la edad al comenzar a trabajar era menor de 18 años.  
     ```python
     df = df[df['person_age'] - df['person_emp_length'] >= 18]
     ```

3. **Detección y manejo de outliers**  
   - Se ajustaron variables con distribuciones sesgadas (ej. ingresos muy altos).  
   - Se exploraron histogramas y boxplots para validar.

4. **Codificación de variables categóricas**  
   - Se convirtieron las variables tipo texto a formato numérico con `pd.get_dummies()`.

---

## 📈 Visualización exploratoria

Algunas de las gráficas utilizadas:

- **Mapa de correlaciones** entre variables numéricas.  
- **Boxplots** para analizar la relación entre ingresos, tasa de interés y riesgo crediticio.  
- **Distribuciones** para detectar valores extremos.

Ejemplo:

```python
sns.boxplot(data=df, x='loan_status', y='person_income')
plt.title('Ingresos vs Riesgo Crediticio')
````

---

## 🤖 Modelo predictivo

Se utilizó un modelo de **Random Forest Classifier**, que combina múltiples árboles de decisión para lograr predicciones más robustas y estables.

Ventajas del modelo:

* Soporta datos con diferentes tipos de variables.
* No requiere escalado previo.
* Reduce el sobreajuste al promediar múltiples árboles.

---

## 📉 Resultados del modelo

**Métricas obtenidas tras el preprocesamiento:**

```
Accuracy: 0.93

Reporte de clasificación:
              precision    recall  f1-score   support

           0       0.92      0.99      0.96      5168
           1       0.96      0.72      0.82      1549

    accuracy                           0.93      6717
   macro avg       0.94      0.86      0.89      6717
weighted avg       0.93      0.93      0.93      6717
```

📊 El modelo predice correctamente más del **93 % de los casos**, con alta precisión al detectar riesgos, aunque se pueden explorar ajustes para mejorar el *recall*.

---

## 🧠 Conexión con Inteligencia Artificial

Este análisis es un ejemplo de cómo la **IA aprende patrones** a partir de datos históricos para **anticipar comportamientos futuros** (en este caso, el riesgo de incumplimiento).
No se programan reglas fijas, sino que el modelo **aprende automáticamente** de los datos.

---

## 🚀 Cómo ejecutar el proyecto

1. Abre el notebook en [Google Colab](https://colab.research.google.com/github/JonathanJulDiaz/devfest-demo/blob/main/credit_risk_analysis.ipynb).
2. Carga el archivo `credit_risk_dataset.csv`.
3. Ejecuta las celdas paso a paso:

   * Carga de datos
   * Limpieza
   * Visualización
   * Entrenamiento del modelo
   * Evaluación

---

## 💬 Créditos

Proyecto de demostración para **Google DevFest**, creado con fines educativos.
Autor: *[Tu nombre]*
Lenguaje: **Python 3 + Google Colab**
Bibliotecas principales: `pandas`, `numpy`, `seaborn`, `matplotlib`, `sklearn`.

---

📘 *Este repositorio busca mostrar cómo el análisis predictivo puede transformar datos crudos en decisiones informadas mediante modelos de Inteligencia Artificial.*

```
```
