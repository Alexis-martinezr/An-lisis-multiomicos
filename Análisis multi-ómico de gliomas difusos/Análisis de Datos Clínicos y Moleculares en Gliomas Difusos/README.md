# 🧠 Análisis de Datos Clínicos y Moleculares en Gliomas Difusos

Este proyecto se centra en la exploración de datos clínicos y moleculares de pacientes con **gliomas difusos**, con el objetivo de identificar patrones relevantes relacionados con características clínicas y moleculares sin entrar en análisis ómicos complejos.

> ⚠️ **Estado:** Análisis en progreso; futuras actualizaciones incluirán integración con transcriptómica y proteómica.

---

## 📊 Descripción del Dataset

- **Gliomas difusos:** representan el 80% de los tumores cerebrales malignos en adultos.  
- **Clasificación histológica:** oligodendroglioma, oligoastrocytoma, astrocytoma y glioblastoma.  
- **Grado tumoral:** II a III, según criterios histológicos de la WHO.  
- **Variabilidad:** alta variabilidad intra- e inter-observador, especialmente en tumores de grado II-III.  
- **Origen de los datos:** The Cancer Genome Atlas (TCGA).  

---

## 🧬 Variables Analizadas

| Variable               | Tipo/Valores relevantes |
|------------------------|------------------------|
| years_to_birth         | numérico               |
| gender                 | categórico             |
| histological_type      | categórico             |
| race                   | categórico             |
| ethnicity              | categórico             |
| radiation_therapy      | categórico             |
| Grade                  | II-III                  |
| Mutation.Count         | numérico               |
| Percent.aneuploidy     | numérico               |
| IDH.status             | categórico             |
| outcome                | dicotómico             |

---

## 📌 Hallazgos Iniciales

1. **Supervivencia por tipo histológico:**  
   - Oligodendroglioma: 100% supervivencia.  
   - Astrocytoma y oligoastrocytoma: 100% mortalidad.  

2. **Radioterapia:**  
   - Los pacientes que recibieron radioterapia mostraron mayor mortalidad relativa, asociada a que la mayoría correspondía a casos con grado histológico más avanzado (G3).  

3. **Edad y subtipo histológico:**  
   - Los pacientes fallecidos tienden a ser más jóvenes, probablemente porque los tipos histológicos más agresivos afectan con mayor frecuencia a pacientes jóvenes.  

4. **Carga mutacional:**  
   - Tendencia a mayor número de mutaciones en pacientes fallecidos, aunque no significativa.  

5. **Estado IDH:**  
   - La mutación en IDH se asocia con mejor pronóstico; los tumores IDH wild-type se vinculan a mayor mortalidad.  

---

## 📊 Resultados de Pruebas de Hipótesis

- **Edad:**  
  - Mann–Whitney U, p = 0.012 → pacientes fallecidos ligeramente más jóvenes que los sobrevivientes.  

- **Número de mutaciones:**  
  - Mann–Whitney U, p = 0.22 → sin diferencia significativa.  

- **Grado y tipo histológico:**  
  - Chi-cuadrada, p < 0.001 → supervivencia significativamente mayor en oligodendroglioma; mortalidad concentrada en astrocytoma y oligoastrocytoma.  
  - Tipo histológico asociado a grado tumoral, p < 0.00001.  

- **Radioterapia:**  
  - Chi-cuadrada, p < 1e-10 → radioterapia asociada a tumores más agresivos.  
  - Comparación de supervivencia por radioterapia: p < 0.001.  

- **Estado IDH:**  
  - Chi-cuadrada, p = 0.003 → mutación IDH asociada a mejor pronóstico.  

- **Sexo, raza y etnia:**  
  - Sin diferencias significativas en supervivencia.  

- **Porcentaje de aneuploidía:**  
  - Mann–Whitney U, p = 0.633 → sin diferencias significativas.  

---

## 🔍 Interpretación Integrada

1. **Edad y tipo histológico:** factores interrelacionados que afectan la supervivencia: los pacientes más jóvenes tienden a presentar gliomas más agresivos.  
2. **Biomarcadores:** mutación en IDH es favorable; tipo histológico y grado tumoral son los principales determinantes de desenlace clínico.  
3. **Variables demográficas:** género, raza y etnia tienen poca influencia individual.  
4. **Tratamiento:** radioterapia refleja la severidad del caso, no un efecto adverso directo.  
5. **Carga mutacional y aneuploidía:** no son determinantes independientes del pronóstico en este cohort.
