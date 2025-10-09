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

## 🔍 Metodología

1. **Análisis univariado:**  
   - Evaluación de distribución de variables clínicas y moleculares 📈  
   - Identificación de **proteínas y genes candidatos** mediante estadística descriptiva y pruebas de significancia 🧫  

2. **Análisis multivariado (en progreso):**  
   - Integración de datos clínicos, transcriptómicos y proteómicos 🔗  
   - Aplicación de **PLS (Partial Least Squares)** para identificar las proteínas más relevantes asociadas a los outcomes clínicos y características moleculares ⚡  

3. **Procesamiento de datos:**  
   - **Python:** pandas, NumPy, Matplotlib, Seaborn 🐍  
   - **R:** análisis multivariado y PLS 📊

---

## 🏷 Resultados preliminares

### Análisis univariado

- **Proteínas candidatas identificadas:** 7 🧪  
- **Genes candidatos identificados:** 2 🧬  

### Análisis multivariado (PLS)

- Se identificaron **68 proteínas con importancia elevada (VIP > 1.0)** 💎, que podrían ser relevantes para caracterizar firmas proteómicas asociadas a gliomas y supervivencia de pacientes.  

> Estos resultados representan un primer conjunto de biomarcadores potenciales y se actualizarán conforme avance el análisis multivariado 🔄

---

## 📋 Conclusiones clínicas preliminares

- **Supervivencia del 100%** en pacientes con **oligodendroglioma** ✅  
- **Mortalidad del 100%** en pacientes con **astrocytoma y oligoastrocytoma** ❌  
- Pacientes que recibieron **radioterapia** mostraron mayor mortalidad relativa ⚠️, probablemente porque correspondían a casos con **grado histológico más avanzado (G3)**  

> Estos hallazgos clínicos proporcionan un contexto para interpretar los resultados moleculares y orientar análisis posteriores 🧠💡

---

## 🛠 Tecnologías y Herramientas

- **Lenguajes:** Python 🐍, R 📊  
- **Librerías Python:** pandas, NumPy, Matplotlib, Seaborn, SciPy  
- **Análisis estadístico:** univariado y multivariado  
- **Visualización:** gráficos de distribución, heatmaps 🌡️ y correlaciones 🔗  

---

## 👤 Autor

**Alexis Gerardo Martínez Rangel**  
TripleTen Data Analyst Program 🎓
