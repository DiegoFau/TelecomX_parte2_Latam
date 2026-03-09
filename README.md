# Telecom X - Parte 2  
## Predicción de cancelación de clientes (Churn)

## 1. Descripción del proyecto

Este proyecto corresponde a la segunda parte del análisis de datos para **Telecom X**, cuyo objetivo es identificar los factores que influyen en la cancelación de clientes (*customer churn*) y construir modelos predictivos capaces de anticipar este comportamiento.

La cancelación de clientes representa un problema crítico para las empresas de telecomunicaciones, ya que adquirir nuevos clientes suele ser más costoso que retener a los existentes. Por este motivo, comprender los factores que influyen en el churn permite desarrollar estrategias de retención más efectivas.

El objetivo principal de este análisis es **predecir la cancelación de clientes utilizando variables relevantes del comportamiento y características del servicio**, aplicando modelos de aprendizaje automático como **regresión logística y árboles de decisión**.

---

# 2. Preparación de los datos

Antes de entrenar los modelos, se realizó un proceso de preparación y transformación de los datos.

## 2.1 Clasificación de variables

Las variables del dataset fueron clasificadas en dos tipos principales:

### Variables categóricas

Corresponden a variables que representan categorías o atributos cualitativos, por ejemplo:

- gender
- Partner
- Dependents
- InternetService
- Contract
- PaymentMethod
- StreamingTV
- StreamingMovies
- OnlineSecurity
- TechSupport

Estas variables se transformaron mediante **codificación one-hot (dummies)** para que pudieran ser utilizadas por los modelos de machine learning.

### Variables numéricas

Las variables numéricas representan valores cuantitativos, por ejemplo:

- tenure (antigüedad del cliente)
- Charges.Monthly
- Charges.Total
- Cuentas_Diarias

Estas variables se utilizaron directamente para el entrenamiento del modelo.

---

## 2.2 Codificación de variables categóricas

Las variables categóricas se transformaron utilizando **one-hot encoding**, generando variables binarias (0 o 1). Esto permite que los modelos interpreten correctamente las distintas categorías sin asumir un orden entre ellas.

Ejemplo:

```
InternetService
DSL
Fiber optic
No
```

se transforma en:

```
InternetService_DSL
InternetService_Fiber optic
InternetService_No
```

---

## 2.3 Separación de datos de entrenamiento y prueba

Para evaluar correctamente el rendimiento de los modelos, el conjunto de datos se dividió en:

- **Datos de entrenamiento (train set)**: utilizados para entrenar los modelos.
- **Datos de prueba (test set)**: utilizados para evaluar la capacidad de generalización del modelo.

Generalmente se utilizó una división de:

```
80% entrenamiento
20% prueba
```

Esto permite evaluar cómo se comporta el modelo frente a datos que no ha visto previamente.

---

# 3. Modelización

Para el análisis se implementaron dos modelos principales:

## 3.1 Regresión logística

La regresión logística es un modelo estadístico utilizado para problemas de clasificación binaria. En este caso, se utilizó para estimar la probabilidad de que un cliente cancele el servicio.

Ventajas del modelo:

- Interpretabilidad de los coeficientes
- Identificación clara de variables influyentes
- Modelo simple y robusto

Los coeficientes obtenidos permiten analizar cómo cada variable afecta la probabilidad de churn.

---

## 3.2 Árbol de decisión

El árbol de decisión es un modelo basado en reglas que divide el conjunto de datos en función de variables que reducen la impureza en cada nodo.

Ventajas:

- Interpretación visual sencilla
- Identificación de variables más importantes
- Capacidad de capturar relaciones no lineales

La importancia de variables obtenida del árbol permitió identificar los factores más influyentes en la cancelación de clientes.

---

# 4. Análisis exploratorio de datos (EDA)

Durante el análisis exploratorio se realizaron distintos gráficos para comprender mejor el comportamiento de los clientes.

Algunos ejemplos de visualizaciones utilizadas incluyen:

### Distribución de churn

Permite observar la proporción de clientes que cancelaron el servicio frente a aquellos que permanecen activos.

### Relación entre churn y antigüedad del cliente

Se observó que los clientes con menor **tenure** presentan una mayor tasa de cancelación.

### Tipo de contrato y churn

Los clientes con **contratos mensuales** presentan mayor probabilidad de cancelación en comparación con contratos de uno o dos años.

### Importancia de variables

Los modelos identificaron variables clave como:

- tenure
- InternetService_Fiber optic
- Charges.Total
- PaymentMethod_Electronic check
- tipo de contrato

Estas variables muestran una fuerte relación con la cancelación de clientes.

---

# 5. Principales insights del análisis

Los resultados del análisis permitieron identificar algunos factores clave asociados al churn:

- Los clientes con **menor antigüedad** tienen mayor probabilidad de cancelar el servicio.
- Los **contratos mensuales** presentan mayor tasa de cancelación que los contratos de largo plazo.
- El servicio de **fibra óptica** aparece asociado a mayores tasas de churn.
- Los **cargos totales y mensuales** influyen en la decisión de cancelación.
- Algunos **métodos de pago**, como electronic check, presentan mayor relación con churn.

Estos hallazgos pueden ayudar a diseñar estrategias de retención más efectivas.

---

# 6. Cómo ejecutar el proyecto

## 6.1 Requisitos

Para ejecutar el proyecto es necesario instalar las siguientes bibliotecas de Python:

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```

Puedes instalarlas con:

```
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## 6.2 Ejecución del notebook

1. Clonar el repositorio o descargar los archivos del proyecto.
2. Abrir el notebook ubicado en:

```
notebooks/TelecomX_Parte2_Modelos.ipynb
```

3. Asegurarse de que el archivo de datos esté en la carpeta:

```
data/telecom_churn_clean.csv
```

4. Ejecutar las celdas del notebook en orden.

El cuaderno realizará automáticamente:

- carga de datos
- preparación de variables
- entrenamiento de modelos
- evaluación de resultados
- análisis de variables relevantes

---

# 7. Conclusión

Este proyecto demuestra cómo el uso de técnicas de análisis de datos y aprendizaje automático puede ayudar a comprender el comportamiento de los clientes y anticipar la cancelación del servicio.

Los modelos utilizados permitieron identificar factores clave asociados al churn, como la antigüedad del cliente, el tipo de contrato y los cargos del servicio. Estos resultados pueden ser utilizados por las empresas para diseñar estrategias de retención que reduzcan la pérdida de clientes y mejoren la satisfacción del usuario.
