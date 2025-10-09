# Análisis Exploratorio de Firmas Transcriptómicas Asociadas a Metástasis Cerebral en Cáncer de Mama HER2+ mediante Microarrays

## Descripción del Proyecto
Este proyecto aborda el **análisis de datos transcriptómicos** para identificar posibles biomarcadores asociados a **metástasis cerebrales** en pacientes con **cáncer de mama HER2+**. Se utiliza información pública de microarrays del repositorio **GEO (GSE43837)** generada por Vareslija et al. (2013) y publicada en *Breast Cancer Research*. 

El objetivo es explorar la expresión diferencial de genes entre **tumores primarios de mama** y **metástasis cerebrales HER2+**, evaluando firmas génicas relevantes para la progresión metastásica y potenciales biomarcadores predictivos o dianas terapéuticas.

## Objetivos
- Identificar genes con **expresión diferencial significativa** entre tumores primarios y metástasis cerebrales.
- Explorar la aplicabilidad de la **firma BD-L**, relacionada con deficiencia funcional de BRCA1, en la predicción de metástasis cerebrales.
- Generar visualizaciones y análisis que sirvan como **base para futuras validaciones experimentales**.

## Dataset
- **GEO Accession:** [GSE43837](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE43837)
- Tipo: Microarrays de expresión génica
- Muestras: Tumores primarios y metástasis cerebrales HER2+
- Variables principales: niveles de expresión génica de 61,359 transcritos

## Metodología
1. **Análisis inicial con GEO2R (R)**
   - Comparación entre grupos de muestras
   - Obtención de estadísticas de expresión diferencial (valores p y p ajustados)

2. **Procesamiento en Python**
   - Librerías utilizadas: `pandas`, `NumPy`, `Matplotlib`
   - Filtrado de genes significativos
   - Visualización de patrones de expresión
   - Cálculo de puntuaciones asociadas a firmas transcriptómicas

3. **Exploración de firmas génicas**
   - Comparación con la **firma BD-L** y evaluación de patrones relacionados con metástasis y respuesta terapéutica

## Resultados
Aunque **ningún gen alcanzó significancia tras corrección por p ajustado**, se identificaron **20 genes con cambios de expresión relevantes** (logFC significativo) que podrían ser **biomarcadores potenciales**:

**COL10A1, ATP6V0C, ZNF391, PPM1H, RGL3, HSD17B4, PSMD5-AS1, ASPN, COL3A1, DNTT, TMEM185A, UBR2, CCL13, SERPINB13, POSTN, IL21R, HERC6, TAS2R41, BRD8**

- De los 61,359 transcritos detectados, 12,499 no fueron identificados, algunos de los cuales podrían corresponder a **antígenos tumorales específicos** derivados de transcripciones no canónicas, alteraciones epigenéticas, cambios de marco de lectura, empalmes aberrantes o fusiones génicas.
- La firma BD-L muestra un patrón de expresión coherente con tumores con **deficiencia de BRCA1**, correlacionando con metástasis cerebrales y respuesta a inhibidores de PARP y temozolomida.

## Conclusiones
- Los 20 genes identificados representan un **punto de partida para estudios experimentales** y validación de biomarcadores.
- La evaluación de transcritos no convencionales podría revelar **nuevas dianas terapéuticas**.
- El análisis proporciona información relevante para **estratificación de riesgo** y posibles intervenciones en cáncer de mama HER2+.

## Tecnologías y Herramientas
- **Lenguajes y Librerías:** Python (`pandas`, `NumPy`, `Matplotlib`), R (`GEO2R`)
- **Técnicas:** Análisis de expresión diferencial, visualización de datos, filtrado de genes, análisis de firmas transcriptómicas

## Autor
**Alexis Gerardo Martínez Rangel**
