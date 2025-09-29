# 2. Modelado Predictivo y Análisis de Escenarios
## Resumen Ejecutivo

Esta sección aborda la construcción de un modelo de regresión para predecir las emisiones de $\text{CO}_2$ basado en los 76 indicadores socioeconómicos y ambientales limpiados en la Pregunta 1. Se evaluaron tres modelos (Regresión Lineal, Random Forest y Gradient Boosting) para seleccionar el más apto para el **Análisis de Escenario** solicitado.

La **Regresión Lineal** fue seleccionada como el **mejor modelo** debido a su capacidad superior para explicar la varianza (mayor $R^2$) y su menor penalización de errores grandes (menor $RMSE$) en este conjunto de datos. Este modelo se utilizó para simular el impacto de un **aumento del 10% en el PIB** en las emisiones de $\text{CO}_2$.

---

## 🛠️ Metodología de Modelado Predictivo

### 1. Preparación y División de Datos
1.  **Variables:** Se definió la variable objetivo ($y$) como las emisiones de $\text{CO}_2$ (`OWID_CB_CO2`). Los **76 indicadores** restantes de la Tabla Dinámica 2 se utilizaron como variables predictoras ($X$).
2.  **División:** El *dataset* fue dividido en un 80% para **entrenamiento** y 20% para **prueba**, asegurando la evaluación del rendimiento del modelo con datos no vistos.

### 2. Modelos Evaluados
Se entrenaron tres modelos de regresión para evaluar el mejor equilibrio entre rendimiento y complejidad:
* **Regresión Lineal (Linear Regression)**
* **Random Forest Regressor**
* **Gradient Boosting Regressor**

### 3. Comparación y Selección del Mejor Modelo
Se compararon las métricas de evaluación ($R^2$, $MAE$, $MSE$, $RMSE$) en el conjunto de prueba:

| Modelo | MAE (Error Absoluto) | MSE (Error Cuadrático Medio) | RMSE (Raíz del Error Cuadrático) | $R^2$ Score (Varianza Explicada) |
| :--- | :--- | :--- | :--- | :--- |
| **Linear Regression** | 2.3607 | **51.2869** | **7.1614** | **0.999954** |
| Random Forest Regressor | **1.9570** | 582.1782 | 24.1283 | 0.999483 |
| Gradient Boosting Regressor | 4.3114 | 61.0652 | 29.3439 | 0.999235 |

**Justificación de la Elección:**
Aunque el **Random Forest Regressor** mostró el menor Error Absoluto Medio ($MAE$), el modelo de **Regresión Lineal** fue seleccionado como el mejor en el contexto de este problema por:
1.  **Mayor Capacidad Explicativa ($R^2$ Score):** Con un $R^2$ de **0.999954**, el modelo de Regresión Lineal explica una porción superior de la variabilidad en las emisiones.
2.  **Menor Error en Errores Grandes ($RMSE$):** Un $RMSE$ significativamente más bajo (**7.16**) indica que el modelo minimiza los errores de predicción más grandes, un factor crucial para la estabilidad en el análisis de escenarios estratégicos.
3.  **Simplicidad e Interpretabilidad:** Dado el alto rendimiento, la simplicidad inherente de la Regresión Lineal facilita la interpretación de los coeficientes para el análisis de escenarios (Pregunta 3).

---

## 🔮 Análisis de Escenario: Impacto del 10% de Aumento del PIB

El modelo de Regresión Lineal fue interpretado mediante sus **coeficientes**, los cuales indican la magnitud y dirección de la relación lineal entre cada variable y las emisiones de $\text{CO}_2$, manteniendo otras variables constantes.

### Simulación y Conclusión
Se simuló un escenario donde el PIB (`OWID_CB_GDP`) aumenta en un 10% para **todas las entradas** en el *dataset* de prueba, manteniendo los demás factores constantes.

**Conclusión del Escenario:**
El modelo predijo una **disminución promedio y total en las emisiones de $\text{CO}_2$** como resultado del incremento del 10% en el PIB. Este resultado, si bien requiere una validación causal más profunda, indica que, bajo las condiciones de esta simulación lineal:

* El **efecto marginal negativo** de otras variables (como la eficiencia energética o los cambios en la matriz económica, cuyos coeficientes en el modelo son negativos) es lo suficientemente fuerte como para **compensar** el impulso positivo en las emisiones que históricamente se asocia con el crecimiento del PIB.
* El modelo sugiere que las relaciones subyacentes capturadas por el *dataset* indican un **desacoplamiento** incipiente entre el crecimiento económico y las emisiones de $\text{CO}_2$.

---

## 🔗 Ver Código y Resultados Detallados

Para revisar la selección de variables, la división de los datos, el código de entrenamiento de los tres modelos, las métricas completas y la simulación del escenario de impacto del PIB, por favor, acceda al Notebook principal:


**[Ver la Sección 2: Predictive Modeling and Scenario Analysis en el Notebook completo](https://colab.research.google.com/drive/1PvvgftZqU8oRfxvQzB_P8Osi0-a4goSz?usp=sharing)*

