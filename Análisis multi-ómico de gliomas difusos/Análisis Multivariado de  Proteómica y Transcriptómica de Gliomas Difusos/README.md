# Análisis Multivariado de  Proteómica y Transcriptómica de Gliomas Difusos
Este proyecto explora la relación entre la expresión de genes y proteínas en gliomas difusos, utilizando métodos multivariados para identificar biomarcadores potenciales y firmas moleculares asociadas a características clínicas.

## Dataset Ómico

- Proteómica: expresión relativa de 174 proteínas involucradas en señalización y regulación celular.

- Transcriptómica: expresión de 145 transcritos.

Datos preprocesados: normalizados y escalados para análisis multivariado.

## Metodología

- Se utilizó Partial Least Squares (PLS) para integrar datos transcriptómicos y proteómicos y asociarlos a outcomes clínicos.

- Se calculó el VIP (Variable Importance in Projection) para identificar las variables más relevantes.

- Se consideraron relevantes las proteínas y genes con VIP > 1.0.

## Resultados Principales

### Proteínas relevantes: 46

Top 10 Proteínas por VIP
| Rank | Proteína    | VIP   |
|------|------------|-------|
| 1    | Syk_p       | 2.047 |
| 2    | YAP_pS127_p | 1.887 |
| 3    | AR_p        | 1.840 |
| 4    | ACC_pS79_p  | 1.624 |
| 5    | 53BP1_p     | 1.582 |
| 6    | DJ-1_p      | 1.570 |
| 7    | ACC1_p      | 1.546 |
| 8    | YAP_p       | 1.537 |
| 9    | HER3_pY1289_p | 1.521 |
| 10   | c-Kit_p     | 1.477 |


### Genes relevantes: 69

Top 10 Genes por VIP
| Rank | Gen       | VIP   |
|------|-----------|-------|
| 1    | STAT5A    | 2.327 |
| 2    | YBX1      | 2.326 |
| 3    | XRCC1     | 2.197 |
| 4    | RPS6KA1   | 2.192 |
| 5    | PARK7     | 2.167 |
| 6    | ACACA     | 2.080 |
| 7    | SYK       | 2.066 |
| 8    | FASN      | 2.060 |
| 9    | NRAS      | 1.977 |
| 10   | PRKCD     | 1.948 |


Estos resultados representan las variables ómicas más influyentes en los outcomes clínicos y podrían constituir un primer conjunto de biomarcadores potenciales.

## Tecnologías y Herramientas

- Lenguajes: Python

- Librerías Python: pandas, NumPy, Matplotlib, Seaborn, scikit-learn

- Análisis multivariado: PLS, VIP

