# 🧠 Integración clínica, transcriptómica y proteómica para el análisis de gliomas - Análisis Univariado, Multivariado y Machine Learning

Este proyecto tiene como objetivo explorar e integrar datos clínicos, transcriptómicos y proteómicos en **gliomas difusos**, con el fin de identificar **biomarcadores** relevantes y desarrollar modelos predictivos del estado clínico del paciente mediante **machine learning**.

Se aplicaron enfoques **univariados** y **multivariados** para la selección de biomarcadores, además de comparar el desempeño de distintos modelos de clasificación.  
El propósito general fue determinar si la integración ómica mejora la predicción de **supervivencia** frente a métodos estadísticos convencionales.

> ⚠️ **Estado:** El análisis se encuentra avanzado, pero continúa en mejora y ampliación de resultados.

---

## 📊 Dataset

El dataset proviene de **Kaggle**, basado en datos generados por **The Cancer Genome Atlas (TCGA)** para gliomas difusos en adultos.

### Información general:
- Los **gliomas difusos** representan aproximadamente el 80% de los tumores cerebrales malignos 🧠  
- Clasificación histológica:  
  - **Oligodendroglioma** 🟦  
  - **Oligoastrocytoma** 🟪  
  - **Astrocitoma** 🟥  
  - **Glioblastoma** 🟧  
- Grado tumoral: II a IV (criterios OMS) ⚖️  
- Alta **variabilidad histopatológica intra- e inter-observador** ⚠️  
- Datos disponibles: **clínicos**, **transcriptómicos** y **proteómicos** 🔬  

---

## 🧬 Tipos de datos incluidos

- **Datos clínicos:** edad, género, tipo histológico, raza, etnia, radioterapia, grado tumoral, recuento de mutaciones, porcentaje de aneuploidía, estado de IDH y outcome.  
- **Proteómica:** 174 proteínas normalizadas relacionadas con señalización celular ⚛️  
- **Transcriptómica:** 145 transcritos normalizados (microarrays) 🧪  

---

## 1. Análisis de Datos Clínicos y Moleculares

**Objetivo:** Explorar las variables clínicas y moleculares, identificando patrones y asociaciones con el outcome clínico.

### Variables Analizadas

| Variable           | Tipo / Valores relevantes |
|--------------------|---------------------------|
| years_to_birth     | Numérico                  |
| gender             | Categórico                |
| histological_type  | Categórico                |
| radiation_therapy  | Categórico                |
| Grade              | II–IV                     |
| Mutation.Count     | Numérico                  |
| Percent.aneuploidy | Numérico                  |
| IDH.status         | Categórico                |
| outcome            | Dicotómico (0 = Vivo / 1 = Muerto) |

### 📈 Resultados de Pruebas de Hipótesis

| Comparación | Prueba | Estadístico / χ² | p-valor | Interpretación |
|--------------|--------|------------------|---------|----------------|
| Mutaciones: vivos vs fallecidos | Mann–Whitney U | 10295.5 | 0.220 | No significativa |
| Edad: vivos vs fallecidos | Mann–Whitney U | 13125.5 | **0.012** | Fallecidos ligeramente más jóvenes |
| Grado II vs III | Chi-Cuadrada | 9.65 | **0.0019** | Diferencia significativa |
| Grado vs tipo histológico | Chi-Cuadrada | 23.36 | **8.4e-06** | Asociación significativa |
| Radioterapia vs grado | Chi-Cuadrada | 42.98 | **5.5e-11** | Asociada a tumores más agresivos |
| Radioterapia vs tipo histológico | Chi-Cuadrada | 23.93 | **6.3e-06** | Diferencia significativa |
| Radioterapia vs supervivencia | Chi-Cuadrada | 13.71 | **0.0002** | Asociada a peor supervivencia |
| Género vs supervivencia | Chi-Cuadrada | 0.028 | 0.865 | No significativa |
| Raza vs supervivencia | Chi-Cuadrada | 1.06 | 0.588 | No significativa |
| Etnia vs supervivencia | Chi-Cuadrada | 0.987 | 0.320 | No significativa |
| IDH vs supervivencia | Chi-Cuadrada | 8.73 | **0.003** | Asociación significativa |
| Aneuploidía: vivos vs fallecidos | Mann–Whitney U | 10862.0 | 0.633 | No significativa |
| Edad vs tipo histológico | ANOVA | 3.29 | **0.038** | Diferencia significativa entre tipos |

🧠 Los resultados sugieren que los pacientes más jóvenes tienden a presentar **gliomas más agresivos** (p < 0.05), y que la mutación en **IDH** se asocia con **mejor pronóstico**.

### Conclusiones Parciales

1. Supervivencia del 100% en pacientes con **oligodendroglioma**.  
2. Mortalidad del 100% en pacientes con **astrocitoma** y **oligoastrocytoma**.  
3. La **radioterapia** se asocia a mayor mortalidad, reflejando su uso en tumores más agresivos.  

---

## 2. Análisis Univariado de Datos Ómicos

**Objetivo:** Identificar proteínas y genes cuya expresión se asocie significativamente con el outcome clínico individualmente.

### Metodología

- Evaluación de significancia con `adj.P.Val < 0.05`  
- Estimación de magnitud del cambio mediante `log2 Fold Change (logFC)`  

### Resultados Ejemplo

**Proteínas significativas**

| Protein       | adj.P.Val | logFC  |
|---------------|-----------|--------|
| Src_pY416_p   | 0.0177    | 7.463  |
| EGFR_pY1068_p | 0.0037    | 4.844  |
| p27_p         | 0.00088   | -3.858 |

**Genes significativos**

| Gene.symbol | adj.P.Val | logFC  |
|--------------|-----------|--------|
| STAT5A       | 3.07e-12  | 0.870  |
| RPS6KA1      | 5.62e-11  | 0.917  |
| SYK          | 4.48e-10  | 0.955  |

---

## 3. Análisis Multivariado (Integración Proteómica y Transcriptómica)

**Objetivo:** Integrar los datos ómicos usando **Partial Least Squares (PLS)** y calcular los valores **VIP (Variable Importance in Projection)** para identificar variables relevantes.

### Metodología

- PLS aplicado a datos normalizados y combinados (proteómica + transcriptómica)  
- Selección de biomarcadores con **VIP > 1.0**  

### Top 10 Biomarcadores

**Proteínas**

| Rank | Proteína    | VIP   |
|------|--------------|-------|
| 1    | Syk_p        | 2.047 |
| 2    | YAP_pS127_p  | 1.887 |
| 3    | AR_p         | 1.840 |

**Genes**

| Rank | Gen       | VIP   |
|------|-----------|-------|
| 1    | STAT5A    | 2.327 |
| 2    | YBX1      | 2.326 |
| 3    | XRCC1     | 2.197 |

---

## 4. Predicción del Estado de Pacientes mediante Machine Learning

**Objetivo:** Predecir el estado clínico (vivo/muerto) de pacientes con gliomas difusos utilizando biomarcadores ómicos y evaluar el poder predictivo de diferentes modelos.

### Conjuntos de Biomarcadores

1. **Univariado:** Solo biomarcadores del análisis univariado  
2. **Univariado ampliado:** Biomarcadores univariados + mutaciones + grado histológico  
3. **Multivariado:** Biomarcadores del análisis multivariado  
4. **Multivariado + PCA:** Reducción a 55 componentes principales  
5. **Multivariado VIP > 1.5:** Selección más estricta  
6. **VIP > 1.5 + PCA:** Reducción a 25 componentes  
7. **Modelo reducido (4 biomarcadores):** STAT5A, RPS6KA1, SYK y AR  

### Modelos Implementados

- **K-Nearest Neighbors (KNN)**  
- **Regresión Logística**  
- **Random Forest**

### Evaluación de Modelos

| Modelo | Biomarcadores | AUC-ROC | Precisión | Observaciones |
|--------|----------------|---------|------------|----------------|
| Regresión Logística | Univariado completo | **0.89** | **0.847** | Mejor desempeño global |
| Regresión Logística | 4 biomarcadores (STAT5A, RPS6KA1, SYK, AR) | **0.88** | **0.8369** | Precisión comparable al modelo completo |

**Matriz de Confusión (Regresión Logística - Modelo Base)**

| Actual \ Predicción | 0 | 1 |
|----------------------|---|---|
| 0                    | 29| 6 |
| 1                    | 9 | 48|

👉 Este resultado demuestra que solo **cuatro biomarcadores** bastan para alcanzar una precisión comparable al modelo completo, evidenciando su alto poder predictivo y relevancia biológica.

---

## 5. 🔎 Análisis de Clusters de Genes y Proteínas

**Objetivo:** Identificar patrones de coexpresión entre genes y proteínas mediante *clustering jerárquico* y análisis de redes.

> ⚠️ Estado: En progreso — el análisis funcional se encuentra en ampliación.

### Metodología
- Estandarización de datos (z-score)
- Clustering jerárquico basado en correlaciones
- Construcción de redes de coexpresión (umbral > 0.5)
- Análisis funcional con **KEGG, GO y Reactome**

### Resultados Principales

| Cluster | Función predominante | Genes/Proteínas Hub | Correlación promedio |
|----------|----------------------|---------------------|----------------------|
| 0 | Reparación de ADN | ATRX, RAD50 | 0.19 |
| 1 | Señalización de EGFR | EGFR_pY1068_p, GRB2 | 0.22 |
| 2 | Regulación inmune y fosforilación | SYK, STAT5A | 0.18 |
| 3 | Apoptosis y transporte mitocondrial | BAX, YBX1 | 0.25 |

---

## 💡 Conclusión General

Este pipeline integral demuestra que:

1. Es posible correlacionar características **clínicas, proteómicas y transcriptómicas** con los outcomes clínicos en gliomas difusos.  
2. Los biomarcadores identificados mediante **PLS-VIP** y **análisis univariado** tienen alto poder predictivo.  
3. La **Regresión Logística** basada en biomarcadores univariados ofrece el mejor desempeño (AUC-ROC = 0.89, Precisión = 84.7%).  
4. Un modelo reducido con solo cuatro biomarcadores (STAT5A, RPS6KA1, SYK y AR) alcanza resultados comparables (AUC-ROC = 0.88, Precisión = 83.69%), demostrando su potencial como **firma molecular pronóstica**.  
5. La integración futura de estos biomarcadores con **datos clínicos tradicionales** podría mejorar aún más la aplicabilidad del modelo en diagnóstico y seguimiento oncológico.

---

## ⚙️ Tecnologías y Herramientas

- **Lenguaje:** Python 🐍  
- **Librerías:** pandas, NumPy, SciPy, scikit-learn, Matplotlib, Seaborn  
- **Procesamiento:** normalización, escalado, PCA  
- **Análisis multivariado:** PLS, VIP  
- **Evaluación estadística:** AUC-ROC, matriz de confusión, precisión  


