# Semana 3 - Evaluación Sumativa 3

## Modelamiento predictivo integrado de `RainTomorrow`

**Curso:** MCDI501 - Estadística Computacional para la Toma de Decisiones  
**Grupo:** 6  
**Integrantes:** Eduardo Contreras; Gonzalo Bouldres; Luis Díaz Giral  
**Docente:** Dr. Jean Paul Maidana González  
**Semilla reproducible:** `5012026`

---

## 1. Descripción general

La Semana 3 corresponde a la Fase 4 de cierre y comunicación del proyecto. Integra los resultados obtenidos en S1 y S2 para construir, diagnosticar y evaluar modelos de regresión logística destinados a predecir `RainTomorrow`.

El flujo incluye manejo de datos faltantes, imputación mediante regresiones explícitas, comparación de tres estrategias de tratamiento, preparación sin fuga de información, construcción de tres modelos logísticos, selección interna, diagnóstico de supuestos, evaluación predictiva, bootstrap de coeficientes, análisis del impacto de la imputación y sensibilidades espacial, temporal y frente a outliers.

El notebook fue ejecutado completamente. Contiene 60 celdas, de las cuales 36 son de código y 24 de texto; las celdas de código presentan numeración consecutiva 1-36 y no registran errores de ejecución.

---

## 2. Objetivo de la entrega

Desarrollar un proyecto final integrado que aplique regresión lineal múltiple para imputación y regresión logística para clasificación, utilizando de manera explícita y trazable los resultados de S1 y S2, y comunicando los hallazgos mediante un notebook reproducible, un informe técnico de máximo diez páginas y un repositorio organizado.

---

## 3. Progresión S1 -> S2 -> S3

La integración metodológica se sustenta en:

- la auditoría y los porcentajes de datos faltantes obtenidos en S1;
- la matriz de correlaciones construida en S1;
- las relaciones priorizadas y evaluadas mediante remuestreo en S2;
- el diagnóstico de outliers y los análisis de robustez de S2;
- la prevalencia y los parámetros estimados en las fases anteriores;
- el cierre computacional de la retroalimentación de S2 dentro del notebook maestro de S3.

S3 no modifica retrospectivamente los resultados oficiales de S1 o S2. Las transformaciones, la imputación, la estandarización, la selección y el umbral predictivo se estiman utilizando entrenamiento o predicciones out-of-fold.

---

## 4. Estructura de la carpeta

```text
semana3/
├── data/
│   ├── raw/
│   │   └── .gitkeep
│   └── processed/
│       └── weatherAUS_sumativa3_modelamiento.csv
├── docs/
│   ├── figures/                         # 24 figuras PNG
│   ├── tables/                          # 107 archivos CSV
│   ├── informe_sumativa3_rain_australia_g6.docx
│   └── informe_sumativa3_rain_australia_g6.pdf
├── notebooks/
│   └── Sumativa3_Rain_Australia_G6.ipynb
├── README.md
├── requirements.txt
├── LICENSE
└── .gitignore
```

La carpeta `data/raw/` permanece vacía porque S3 no incorpora una fuente nueva. El notebook utiliza el dataset original de S1 y las evidencias exportadas por S1 y S2.

---

## 5. Datos utilizados

### 5.1 Insumos

```text
semana1/data/raw/weatherAUS.csv
semana1/docs/tables/03_auditoria_datos_faltantes.csv
semana1/docs/tables/06_matriz_correlacion_pearson.csv
semana2/docs/tables/04b_diagnostico_estabilidad_correlaciones.csv
semana2/docs/tables/04c_multicolinealidad_predictoras.csv
semana2/docs/tables/05b_sensibilidad_montecarlo.csv
semana2/docs/tables/08b_diagnostico_outliers_iqr.csv
semana2/docs/tables/09b_sintesis_robustez.csv
semana2/docs/tables/10_resultados_validados_para_s3.csv
```

### 5.2 Base procesada

```text
semana3/data/processed/weatherAUS_sumativa3_modelamiento.csv
```

Características verificadas:

- 142.193 observaciones y 34 columnas;
- 99.535 registros de entrenamiento y 42.658 de prueba;
- cero filas duplicadas y cero identificadores `row_id` duplicados;
- cero faltantes en las variables utilizadas por los modelos;
- prevalencia de `RainTomorrow = Yes` de 22,418 % en ambos conjuntos por estratificación.

La base conserva variables auxiliares excluidas del modelamiento; estas pueden mantener valores faltantes sin afectar el pipeline final.

---

## 6. Notebook principal

```text
semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb
```

El notebook:

1. resuelve automáticamente la raíz del repositorio;
2. valida la existencia de los insumos obligatorios de S1 y S2;
3. elimina y regenera las salidas computacionales de S3;
4. controla versiones, semillas, tamaños muestrales y ausencia de fuga;
5. detiene la ejecución ante inconsistencias metodológicas o artefactos faltantes;
6. genera un manifiesto final con tamaño y SHA-256.

---

## 7. Metodología aplicada

### 7.1 Manejo de datos faltantes

S1 identificó dieciséis variables numéricas continuas con faltantes. Diez forman parte de la matriz correlacional entregada en S1 y constituyen el conjunto analítico trazable de S3:

```text
MinTemp, MaxTemp, Rainfall, WindGustSpeed,
Humidity9am, Humidity3pm, Pressure9am, Pressure3pm,
Temp9am, Temp3pm
```

Para cada una se ajustó una regresión lineal múltiple explícita con tres a cinco predictores disponibles en la matriz de S1. `Rainfall` se modeló en escala `log1p` y se retransmitió mediante el factor de *smearing* de Duan. `RainToday_bin` se imputó mediante regresión logística y `RainTomorrow` no se imputó.

Las seis variables numéricas restantes con faltantes (`Evaporation`, `Sunshine`, `WindSpeed9am`, `WindSpeed3pm`, `Cloud9am` y `Cloud3pm`) se contabilizaron y excluyeron antes de comparar estrategias, porque no integran la matriz correlacional entregada en S1 ni la validación de S2. La cobertura y la justificación se documentan en `03b` y `03f`.

Se compararon de forma simétrica:

1. casos completos;
2. imputación simple con parámetros de entrenamiento;
3. imputación secuencial determinística mediante regresiones explícitas.

### 7.2 Preparación para clasificación

- partición 70/30 estratificada antes de imputar, escalar o seleccionar;
- conservación de extremos meteorológicamente plausibles;
- transformación `log1p` de `Rainfall` y sensibilidad por winsorización 1-99 %;
- estandarización estimada exclusivamente con entrenamiento;
- codificación dummy de `Season`, con `Summer` como referencia;
- exclusión de redundancias fuertes antes de la selección automática;
- evaluación complementaria de `Location` por su alta cardinalidad.

### 7.3 Tres modelos logísticos

- **M1 S1/S2:** especificación fija guiada por evidencia previa.
- **M2 stepwise AIC:** selección *forward* por bloques.
- **M3 BIC parsimonioso:** búsqueda exhaustiva de subconjuntos jerárquicamente válidos.

La comparación interna utiliza validación cruzada anidada. La selección inferencial se realiza con `statsmodels` sin ponderación. La evaluación clasificatoria compara configuraciones no ponderadas y balanceadas mediante predicciones out-of-fold.

### 7.4 Diagnóstico y estabilidad

Se evaluaron:

- VIF y resolución explícita de multicolinealidad;
- linealidad en el logit mediante Box-Tidwell y términos cuadráticos jerárquicos;
- residuos de devianza, leverage y distancia de Cook;
- suficiencia muestral y señales numéricas de separación;
- errores robustos agrupados por `Location`;
- bootstrap no paramétrico de 10.000 réplicas para coeficientes y odds ratios.

### 7.5 Sensibilidades

- tres estrategias de imputación;
- winsorización;
- ponderación de clases y umbral;
- incorporación de `Location`;
- validación temporal;
- eliminación de observaciones influyentes.

---

## 8. Resultados principales

- Estrategia seleccionada: `imputacion_regresion`.
- Modelo inferencial seleccionado sin test: `M3_BIC_parsimonioso`.
- Especificación definitiva: `sin_RainToday_bin`.
- VIF máximo definitivo: 4,7897.
- Configuración clasificatoria: balanceada, con umbral OOF 0,60.
- Prueba: accuracy 0,8183; precision 0,5831; recall 0,6642; F1 0,6210; ROC-AUC 0,8525; PR-AUC 0,6727.
- Bootstrap: 10.000 de 10.000 réplicas exitosas.
- Parámetros inestables bajo bootstrap fila a fila: cero.
- Efectos sensibles a errores robustos por `Location`: `MaxTemp` y `MaxTemp_sq`.
- Efectos cuya conclusión cambia entre imputaciones: `MaxTemp` y `MaxTemp_sq`.
- Validación temporal: ROC-AUC 0,8453 y F1 0,6129.

El modelo no ponderado se utiliza para interpretar probabilidades y odds ratios, debido a su mejor calibración. La configuración balanceada se utiliza para clasificación y para aplicar el umbral operativo.

---

## 9. Salidas generadas

La ejecución produjo:

- **107 CSV** en `docs/tables/`: 106 tablas previas al manifiesto y el propio control `44`;
- **24 figuras PNG** en `docs/figures/`;
- **una base procesada** en `data/processed/`;
- **un notebook ejecutado** con 36 celdas de código consecutivas y sin errores.

Las tablas se agrupan de la siguiente forma:

| Rango | Contenido |
|---|---|
| `00`-`12b` | entorno, trazabilidad, faltantes e imputación |
| `13`-`23b` | preparación, selección y evaluación interna |
| `24`-`30b` | umbral, calibración, diagnóstico e influencia |
| `31a`-`32b` | bootstrap y estabilidad |
| `33`-`41b` | impacto de imputación y sensibilidades |
| `42`-`44` | síntesis, cobertura e integridad |

Las tablas `08c`, `15b`, `20d` y `31b` conservan sus encabezados y cero registros porque no se produjeron advertencias o fallos en esos procedimientos.

---

## 10. Control metodológico e integridad

```text
semana3/docs/tables/43_control_metodologico_rubrica.csv
semana3/docs/tables/43a_matriz_respuesta_retroalimentacion_S2.csv
semana3/docs/tables/44_control_integridad_salidas_sumativa3.csv
```

El manifiesto `44` registra **131 artefactos**: 106 tablas, 24 figuras y una base procesada. Para cada archivo verifica existencia, tamaño y SHA-256. El manifiesto no se auto-incluye, por lo que el directorio `docs/tables/` contiene 107 CSV en total.

---

## 11. Informe final integrado

```text
semana3/docs/informe_sumativa3_rain_australia_g6.docx
semana3/docs/informe_sumativa3_rain_australia_g6.pdf
```

El informe tiene diez páginas y sintetiza la evidencia decisional sin duplicar las 107 tablas del repositorio. Incluye resumen ejecutivo, introducción, metodología integrada, resultados, discusión, conclusiones, recomendaciones y correspondencia con la rúbrica.

---

## 12. Ejecución

Desde la raíz del repositorio, en PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r semana3/requirements.txt
python -m jupyterlab
```

Abrir:

```text
semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb
```

Ejecutar:

```text
Kernel -> Restart Kernel and Run All Cells
```

La validación cruzada anidada y el bootstrap de 10.000 réplicas concentran la mayor parte del tiempo de ejecución.

---

## 13. Dependencias principales

Las versiones exactas se encuentran en `requirements.txt` y corresponden al entorno validado:

- Python 3.12.4;
- NumPy 1.26.4;
- pandas 2.2.2;
- SciPy 1.13.1;
- scikit-learn 1.4.2;
- statsmodels 0.14.2;
- Matplotlib 3.8.4.

---

## 14. Reproducibilidad y alcance

El conjunto de prueba se mantiene reservado durante las decisiones propias de S3. No obstante, S1 y S2 analizaron la base completa antes de definir dicha partición; por ello, el test no se interpreta como validación externa independiente del proceso exploratorio global.

Los resultados son predictivos y asociativos. La repetición por localidad y fecha se aborda mediante diagnósticos y sensibilidades, pero no sustituye una validación externa en nuevas localidades ni un modelo jerárquico espacio-temporal.
