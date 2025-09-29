# 3. Problema de Fermi y Análisis de Sensibilidad (Adopción de VE)
## Resumen Ejecutivo

Este análisis aborda la **Pregunta de Fermi** de estimar el impacto de la adopción masiva de Vehículos Eléctricos (VE) en las emisiones de $\text{CO}_2$. Dado que el *dataset* carece de métricas directas de VE o transporte, se aplicó un **Análisis de Sensibilidad** utilizando el modelo de Regresión Lineal entrenado en la Pregunta 2.

La simulación consistió en aplicar una **reducción del 50%** a los indicadores de emisiones de $\text{CO}_2$ provenientes de **Petróleo y Gas** (indicadores indirectos del sector transporte).

**Hallazgos Clave:** La simulación predice una **reducción total de las emisiones del -4.78%** (-171,245.63 unidades de $\text{CO}_2$). Los **Estados Unidos** y la **Federación Rusa** son los países donde se predice la mayor reducción absoluta, reflejando su dependencia actual de las emisiones de combustibles fósiles.

---

## 🛠️ Metodología del Problema de Fermi y Simulación

### 1. Definición del Problema de Fermi
El objetivo es estimar el impacto de un cambio drástico (**50% de la población mundial adopta VE**) con información limitada. El enfoque metodológico fue:
* **Revisión del Dataset:** Se confirmó la **ausencia de indicadores directos** de adopción de VE o transporte específico.
* **Estimación por Proxy:** Se utilizaron las variables de emisiones de **Petróleo y Gas** como *proxies* indirectos de las emisiones del sector transporte, que es el principal objetivo de la transición a VE.

### 2. Supuestos Críticos para el Análisis de Sensibilidad
Dada la naturaleza de la simulación, se establecieron los siguientes **supuestos y limitaciones**:
| Tipo | Detalle |
| :--- | :--- |
| **Supuestos** | Se aplicó una reducción uniforme del **50.0%** a las variables de $\text{CO}_2$ de Petróleo y Gas (absolutas y per cápita). Esto asume un impacto directo y proporcional. |
| **Limitaciones** | El **modelo es lineal** y puede subestimar o sobreestimar los efectos complejos y no lineales de una transición tecnológica masiva. El cambio está **fuera del rango histórico** de los datos de entrenamiento. |

### 3. Ejecución de la Simulación
Se aplicó la reducción del 50% a los siguientes indicadores dentro del *dataset* utilizado para la predicción con el modelo de Regresión Lineal:
* `OWID_CB_OIL_CO2`
* `OWID_CB_OIL_CO2_PER_CAPITA`
* `OWID_CB_GAS_CO2`
* `OWID_CB_GAS_CO2_PER_CAPITA`

---

## 📊 Resultados del Análisis Predictivo

### Impacto Global de la Adopción de VE
La simulación predice una reducción notable en las emisiones globales de $\text{CO}_2$ basadas en las relaciones históricas capturadas por el modelo lineal:

| Métrica | Cambio Predicho (Linear Regression) |
| :--- | :--- |
| **Cambio Total Predicho en Emisiones** | **-171,245.6306** |
| **Cambio Porcentual Total** | **-4.7840%** |
| **Cambio Promedio Predicho por registro** | **-4.2256** |

El cambio porcentual de **-4.78%** en las emisiones totales de $\text{CO}_2$ subraya que, si bien una reducción en las fuentes de Petróleo y Gas tiene un impacto significativo, este cambio por sí solo no resuelve el problema de las emisiones globales debido a la persistencia de otras fuentes como el Carbón y los procesos industriales.

### Países con Mayor Reducción Absoluta
El análisis de sensibilidad predice que los siguientes países experimentarían las mayores reducciones absolutas de $\text{CO}_2$ en el escenario simulado, debido a su gran volumen actual de emisiones basadas en Petróleo y Gas:

| País | Cambio Predicho de $\text{CO}_2$ (Unidades) |
| :--- | :--- |
| **United States** | -23681.15 |
| **Russian Federation** | -5386.43 |
| **China** | -5076.09 |
| **Japan** | -4600.69 |
| **Germany** | -2838.04 |

---

## 🔎 Interpretación y Próximos Pasos

La simulación sugiere que la adopción masiva de VE es una estrategia efectiva para la mitigación del $\text{CO}_2$, aunque su efecto total se limita a aproximadamente el **4.8%** de las emisiones, en el contexto de las relaciones lineales. Este análisis de sensibilidad es crucial porque:

* **Valida Estrategia:** Cuantifica, bajo un supuesto conservador (modelo lineal), el impacto esperado de la descarbonización del transporte.
* **Prioriza Intervención:** Identifica a **EE. UU., Rusia y China** como los países con el mayor potencial de reducción absoluta a través de la adopción de VE.

**Próximos Pasos:**
El análisis futuro debe centrarse en:
1.  **Explorar Modelos No Lineales:** Para capturar mejor las dinámicas complejas de los cambios tecnológicos.
2.  **Integrar Datos de Generación Eléctrica:** El verdadero impacto de los VE depende de si la electricidad que los alimenta proviene de fuentes renovables o de combustibles fósiles (carbón/gas).

---

## 🔗 Ver Código y Resultados Detallados

Para revisar el código de la simulación del escenario de VE, la manipulación de las variables de Petróleo/Gas y la lista completa de la reducción predicha por país, por favor, acceda al Notebook principal:

**[Ver la Sección 3: Fermi Problem and Sensitivity Analysis en el Notebook completo](https://colab.research.google.com/drive/1PvvgftZqU8oRfxvQzB_P8Osi0-a4goSz#scrollTo=7962b107)*



