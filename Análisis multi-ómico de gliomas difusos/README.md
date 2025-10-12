# 🧠 Integración clínica, transcriptómica y proteómica para el análisis de gliomas - Análisis Univariado y Multivariado

Este proyecto tiene como objetivo explorar la relación entre características clínicas, transcriptómicas y proteómicas en gliomas difusos mediante análisis univariado y multivariado. Se busca identificar genes y proteínas candidatas que puedan actuar como **biomarcadores** o **dianas terapéuticas**, así como correlacionar hallazgos moleculares con información clínica relevante.  

> ⚠️ **Estado:** El análisis está en progreso y se actualizará en futuras versiones del proyecto.

---

## 📊 Dataset

El dataset proviene de **Kaggle**, basado en datos generados por **The Cancer Genome Atlas (TCGA)** para gliomas difusos en adultos.

### Información general:
- Los **gliomas difusos** representan el 80% de los tumores cerebrales malignos 🧠  
- Clasificación histológica:  
  - **Oligodendroglioma** 🟦  
  - **Oligoastrocytoma** 🟪  
  - **Astrocitoma** 🟥  
  - **Glioblastoma** 🟧  
- Grado tumoral: II a IV según criterios de la **OMS** ⚖️  
- La clasificación histopatológica presenta **alta variabilidad intra- e inter-observador** ⚠️, especialmente en tumores de grado II-III  
- Datos disponibles: **clínicos**, **transcriptómicos** y **proteómicos** 🔬

---

## 🧬 Tipos de datos incluidos

- **Datos clínicos:** edad, género, tipo histológico, raza, etnia, terapia de radiación, grado tumoral, recuento de mutaciones, porcentaje de aneuploidía, estado de IDH y outcome  
- **Proteómica:** valores relativos preprocesados de múltiples proteínas involucradas en señalización y regulación celular ⚛️  
- **Transcriptómica:** valores crudos de expresión génica (microarrays) 🧪

---

## 1. Análisis de Datos Clínicos y Moleculares

**Objetivo:** Explorar variables clínicas y moleculares de los pacientes, identificando patrones relevantes sin entrar en análisis ómicos complejos.

### Variables Analizadas

| Variable               | Tipo/Valores relevantes |
|------------------------|------------------------|
| years_to_birth         | numérico               |
| gender                 | categórico             |
| histological_type      | categórico             |
| race                   | categórico             |
| ethnicity              | categórico             |
| radiation_therapy      | categórico             |
| Grade                  | II-IV                  |
| Mutation.Count         | numérico               |
| Percent.aneuploidy     | numérico               |
| IDH.status             | categórico             |
| outcome                | dicotómico             |

### Conclusiones Parciales

1. Supervivencia del 100% en pacientes con oligodendroglioma.  
2. Mortalidad del 100% en pacientes con astrocytoma y oligoastrocytoma.  
3. Radioterapia asociada a mayor mortalidad, correlacionada con tumores de grado avanzado.  

---

## 2. Análisis Univariado de Datos Moleculares

**Objetivo:** Identificar proteínas y genes cuya expresión se asocie significativamente con el outcome clínico mediante análisis univariado.

### Dataset

- Proteómica: 174 proteínas, con imputación y escalado.  
- Transcriptómica: 145 transcritos, normalizados.

### Metodología

- Análisis univariado con `adj.P.Val < 0.05`  
- Evaluación de log2 fold change (`logFC`)  

### Resultados Ejemplo

**Proteínas significativas**

| Protein       | adj.P.Val | logFC  |
|---------------|-----------|--------|
| Src_pY416_p   | 0.0177    | 7.463  |
| EGFR_pY1068_p | 0.0037    | 4.844  |
| p27_p         | 0.00088   | -3.858 |

**Genes significativos**

| Gene.symbol | adj.P.Val | logFC  |
|------------|-----------|--------|
| STAT5A     | 3.07e-12  | 0.870  |
| RPS6KA1    | 5.62e-11  | 0.917  |
| SYK        | 4.48e-10  | 0.955  |

---

## 3. Análisis Multivariado de Proteómica y Transcriptómica

**Objetivo:** Integrar datos ómicos usando PLS y calcular VIP para seleccionar biomarcadores potenciales.

### Metodología

- **PLS (Partial Least Squares)** para correlacionar datos ómicos con outcomes clínicos.  
- **VIP (Variable Importance in Projection):** variables relevantes con VIP > 1.0.

### Resultados Top 10

**Proteínas**

| Rank | Proteína    | VIP   |
|------|------------|-------|
| 1    | Syk_p       | 2.047 |
| 2    | YAP_pS127_p | 1.887 |
| 3    | AR_p        | 1.840 |

**Genes**

| Rank | Gen       | VIP   |
|------|-----------|-------|
| 1    | STAT5A    | 2.327 |
| 2    | YBX1      | 2.326 |
| 3    | XRCC1     | 2.197 |

---

## 4. Predicción del Estado de Pacientes mediante Machine Learning

**Objetivo:** Comparar modelos de ML utilizando biomarcadores univariados y multivariados para predecir el estado clínico y la agresividad tumoral.

### Conjuntos de Biomarcadores

1. Univariado: solo biomarcadores del análisis univariado  
2. Univariado ampliado: biomarcadores univariados + número de mutaciones + grado histológico  
3. Multivariado: biomarcadores del análisis multivariado  
4. Multivariado con PCA (mejor PCA = 55)  
5. Multivariado VIP > 1.5  
6. Multivariado VIP > 1.5 + PCA (mejor PCA = 25)

### Modelos Implementados

- K-Nearest Neighbors (KNN)  
- Regresión Logística  
- Random Forest  

### Evaluación

- **Métricas:** AUC-ROC, Precisión (Accuracy), Matriz de Confusión  
- **Mejor modelo:** Regresión Logística con biomarcadores univariados  
  - AUC-ROC: 0.89  
  - Precisión: 0.847  

**Matriz de Confusión (threshold optimizado por Youden)**

| Actual \ Predicción | 0  | 1  |
|--------------------|----|----|
| 0                  | 29 | 6  |
| 1                  | 9  | 48  |

---

## Tecnologías y Herramientas

- **Lenguaje:** Python 🐍  
- **Librerías:** pandas, NumPy, SciPy, scikit-learn, Matplotlib, Seaborn  
- **Procesamiento:** normalización, escalado, PCA  
- **Análisis multivariado:** PLS, VIP  

---

## Conclusión General

Este pipeline integral demuestra que:

1. Es posible correlacionar características clínicas y moleculares con outcomes clínicos en gliomas difusos.  
2. Los biomarcadores ómicos identificados por análisis univariado y multivariado permiten predecir con alta precisión el estado del paciente.  
3. El modelo más eficiente combina biomarcadores univariados con regresión logística, logrando un **AUC-ROC de 0.89** y **precisión de 0.847**, con menor costo debido al reducido número de biomarcadores.  
4. La integración futura con datos clínicos tradicionales podría mejorar aún más la capacidad predictiva, facilitando la estratificación de pacientes y el desarrollo de estrategias terapéuticas personalizadas.


