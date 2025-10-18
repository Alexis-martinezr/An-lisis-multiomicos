# Análisis Univariado de Datos Moleculares en Gliomas Difusos - Optención de Biomarcadores

Este proyecto se centra en el análisis univariado de datos de expresión proteica y génica en pacientes con gliomas difusos. El objetivo es identificar proteínas y genes cuya expresión se asocie significativamente con el outcome clínico de los pacientes.

⚠️ Estado: Análisis en progreso.

## Dataset

El dataset incluye:

- Proteómica: expresión relativa de 174 proteínas. Se realizó imputación de valores faltantes y escalado de los datos.

- Transcriptómica: expresión de 145 transcritos.

## Metodología

Proteómica:

- Imputación de datos faltantes

- Escalado estándar (z-score)

- Análisis univariado para evaluar la significancia de cada proteína respecto al outcome clínico (adj.P.Val < 0.05).

- Se reporta también el log2 fold change (logFC) para evaluar la magnitud del cambio en expresión.

Resultados Univariados
Proteínas Significativas (adj.P.Val < 0.05)

| Protein           | adj.P.Val   | logFC  |
|------------------|------------|--------|
| Src_pY416_p       | 0.017681   | 7.463  |
| EGFR_pY1068_p     | 0.003745   | 4.844  |
| p27_p             | 0.000876   | -3.858 |
| HER2_pY1248_p     | 0.009947   | 3.676  |
| Cyclin_B1_p       | 0.011747   | 3.378  |
| PRAS40_pT246_p    | 0.009947   | 2.742  |
| 4E-BP1_pS65_p     | 0.036569   | -1.992 |

Transcriptómica:

Análisis univariado por cada gen, usando valores ajustados de p (adj.P.Val) y logFC.

| Gene.symbol | adj.P.Val      | logFC  |
|------------|---------------|--------|
| STAT5A     | 3.07e-12      | 0.870  |
| RPS6KA1    | 5.62e-11      | 0.917  |
| SYK        | 4.48e-10      | 0.955  |
| AR         | 5.44e-07      | 1.111  |
| WWTR1      | 3.26e-04      | 0.908  |
| CAV1       | 2.40e-03      | 1.068  |

Nota: logFC positivo indica sobreexpresión en el grupo de interés; logFC negativo indica subexpresión.

## Tecnologías y Herramientas

- Lenguaje: Python 🐍

- Librerías: pandas, NumPy, SciPy, Matplotlib, Seaborn

- Procesamiento: imputación, escalado, análisis estadístico univariado
