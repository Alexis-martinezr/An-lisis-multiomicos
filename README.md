# 📂 Portafolio de Proyectos Ómicos – Alexis Gerardo Martínez Rangel

Este repositorio reúne proyectos de análisis de datos ómicos, incluyendo transcriptómica, proteómica y su integración con datos clínicos. Cada proyecto es independiente y tiene objetivos específicos relacionados con la identificación de **biomarcadores** y **dianas terapéuticas**.

> ⚠️ **Estado general:** Algunos análisis están en progreso y se actualizarán en futuras versiones.

---

## 1️⃣ Proyecto: Análisis Exploratorio de Firmas Transcriptómicas en Cáncer de Mama HER2+

### 📌 Descripción
Análisis de datos transcriptómicos de microarrays (GEO: GSE43837) para identificar posibles biomarcadores asociados a metástasis cerebrales en cáncer de mama HER2+.

### 🎯 Objetivos
- Identificar genes con expresión diferencial significativa entre tumores primarios y metástasis cerebrales.  
- Explorar la firma BD-L relacionada con deficiencia funcional de BRCA1.  
- Generar visualizaciones y análisis base para futuras validaciones experimentales.

### 🧬 Dataset
- **Tipo:** Microarrays de expresión génica  
- **Muestras:** Tumores primarios y metástasis cerebrales HER2+  
- **Variables principales:** niveles de expresión de 61,359 transcritos  

### 🔍 Metodología
- Análisis inicial con **GEO2R (R)** para comparación entre grupos y obtención de estadísticas (p y p ajustados)  
- Procesamiento en **Python** con pandas, NumPy y Matplotlib para filtrar genes significativos, visualizar patrones de expresión y calcular puntuaciones asociadas a firmas transcriptómicas  
- Evaluación de la firma **BD-L** y patrones relacionados con metástasis y respuesta terapéutica  

### 📊 Resultados
- **Genes relevantes identificados:** 20  
- La firma BD-L mostró un patrón coherente con tumores con deficiencia de BRCA1  
- Algunos transcritos no convencionales podrían representar nuevas dianas terapéuticas  

### ✅ Conclusiones
- Los genes identificados son candidatos a biomarcadores y posibles dianas terapéuticas.  
- La exploración de transcritos no convencionales abre nuevas oportunidades de investigación.  

---

## 2️⃣ Proyecto: Integración Clínica, Transcriptómica y Proteómica en Gliomas

### 📌 Descripción
Integración de datos clínicos, transcriptómicos y proteómicos de gliomas difusos (TCGA) para identificar biomarcadores moleculares y correlacionarlos con outcomes clínicos.

> ⚠️ **Estado:** El análisis multivariado con PLS está en progreso.

### 📊 Dataset
- Datos de **gliomas difusos** adultos (80% de tumores cerebrales malignos)  
- Clasificación histológica: Oligodendroglioma 🟦, Oligoastrocytoma 🟪, Astrocitoma 🟥, Glioblastoma 🟧  
- Datos disponibles: clínicos, proteómicos (valores relativos) y transcriptómicos (valores crudos)

### 🔍 Metodología
1. **Análisis univariado:**  
   - Evaluación de variables clínicas y moleculares  
   - Identificación de proteínas y genes candidatos  
2. **Análisis multivariado (PLS, en progreso):**  
   - Integración de datos clínicos, transcriptómicos y proteómicos  
   - Identificación de proteínas más relevantes (VIP > 1.0)  

### 📊 Resultados preliminares
- **Análisis univariado:** 7 proteínas y 2 genes candidatos  
- **Análisis multivariado:** 68 proteínas con importancia elevada identificadas  

### 📋 Conclusiones clínicas preliminares
- Supervivencia del 100% en pacientes con **oligodendroglioma** ✅  
- Mortalidad del 100% en pacientes con **astrocytoma y oligoastrocytoma** ❌  
- Pacientes con radioterapia mostraron mayor mortalidad relativa, asociada a **grado histológico más avanzado (G3)** ⚠️  

---

## 🛠 Tecnologías y Herramientas Comunes
- **Lenguajes:** Python 🐍, R 📊  
- **Librerías Python:** pandas, NumPy, Matplotlib, Seaborn, SciPy  
- **Análisis estadístico:** univariado y multivariado  
- **Visualización:** gráficos de distribución, heatmaps 🌡️ y correlaciones 🔗  

---

## 👤 Autor
**Alexis Gerardo Martínez Rangel**  
