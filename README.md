# MCDI501 - Estadística Computacional para la Toma de Decisiones

## Proyecto integrado: *Rain in Australia*

**Grupo 6**  
**Integrantes:** Eduardo Contreras · Gonzalo Bouldres · Luis Díaz Giral  
**Docente:** Dr. Jean Paul Maidana González

---

## 1. Descripción general

Este repositorio contiene el desarrollo completo y progresivo de las tres evaluaciones sumativas del curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**, aplicadas al conjunto de datos meteorológicos *Rain in Australia* (`weatherAUS.csv`).

El objetivo general del proyecto es estudiar y predecir la ocurrencia de lluvia al día siguiente, representada por la variable objetivo `RainTomorrow`, mediante una secuencia analítica integrada:

1. **Semana 1:** análisis exploratorio, estadística descriptiva, estimación e inferencia.
2. **Semana 2:** validación computacional mediante remuestreo, simulación Monte Carlo y análisis de robustez.
3. **Semana 3:** imputación mediante regresión, clasificación logística, diagnóstico, evaluación predictiva, bootstrap y comunicación final integrada.

La estructura del repositorio mantiene trazabilidad entre datos originales, bases procesadas, notebooks ejecutados, módulos auxiliares, tablas, figuras, controles de integridad e informes técnicos. La Semana 3 utiliza explícitamente los resultados obtenidos en las semanas anteriores; por tanto, las fases no se presentan como análisis independientes.

---

## 2. Objetivo del proyecto

Desarrollar una solución estadística reproducible para apoyar la predicción de `RainTomorrow`, integrando:

- análisis exploratorio e inferencial;
- validación mediante bootstrap y simulación;
- manejo trazable de datos faltantes;
- regresión lineal múltiple para imputación;
- regresión logística para clasificación;
- selección y diagnóstico de modelos;
- evaluación del desempeño predictivo;
- análisis de estabilidad y sensibilidad;
- comunicación técnica de resultados.

---

## 3. Estructura del repositorio

```text
mcdia501-estadistica-computacional-g6/
├── semana1/
│   ├── data/
│   │   ├── raw/
│   │   └── processed/
│   ├── docs/
│   │   ├── figures/
│   │   ├── tables/
│   │   ├── inventario_outputs_sumativa1.csv
│   │   ├── informe_sumativa1_rain_australia_g6.docx
│   │   └── informe_sumativa1_rain_australia_g6.pdf
│   ├── notebooks/
│   │   └── Sumativa1_Rain_Australia_G6.ipynb
│   ├── src/
│   │   └── estadistica_utils.py
│   ├── README.md
│   ├── LICENSE
│   └── requirements.txt
│
├── semana2/
│   ├── data/
│   │   ├── input/
│   │   └── processed/
│   ├── docs/
│   │   ├── figures/
│   │   ├── tables/
│   │   ├── inventario_outputs_sumativa2.csv
│   │   ├── informe_sumativa2_rain_australia_g6.docx
│   │   └── informe_sumativa2_rain_australia_g6.pdf
│   ├── notebooks/
│   │   └── Sumativa2_Rain_Australia_G6.ipynb
│   ├── src/
│   │   └── remuestreo_utils.py
│   ├── README.md
│   ├── LICENSE
│   └── requirements.txt
│
├── semana3/
│   ├── data/
│   │   ├── raw/
│   │   └── processed/
│   │       └── weatherAUS_sumativa3_modelamiento.csv
│   ├── docs/
│   │   ├── figures/
│   │   ├── tables/
│   │   ├── informe_sumativa3_rain_australia_g6.docx
│   │   └── informe_sumativa3_rain_australia_g6.pdf
│   ├── notebooks/
│   │   └── Sumativa3_Rain_Australia_G6.ipynb
│   ├── README.md
│   ├── LICENSE
│   └── requirements.txt
│
├── README.md
├── CHANGELOG.md
└── .gitignore
```

Cada semana posee documentación y dependencias propias. Los notebooks utilizan rutas relativas y resuelven la raíz del repositorio para conservar la portabilidad del proyecto.

---

## 4. Estado verificado de las entregas

| Fase | Estado | Producto principal |
|---|---|---|
| Semana 1 | Ejecutada y documentada | `semana1/notebooks/Sumativa1_Rain_Australia_G6.ipynb` |
| Semana 2 | Ejecutada y documentada | `semana2/notebooks/Sumativa2_Rain_Australia_G6.ipynb` |
| Semana 3 | Finalizada, ejecutada, verificada y documentada | `semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb` |

Los informes técnicos finales de las tres semanas se encuentran incorporados en formato Word y PDF dentro de sus respectivas carpetas `docs/`.

---

## 5. Semana 1 - Evaluación Sumativa 1

La Semana 1 desarrolla la caracterización exploratoria e inferencial inicial del dataset.

### Metodologías principales

- auditoría de calidad y valores faltantes;
- tipificación de variables;
- estadística descriptiva;
- intervalos de confianza;
- prueba t de Welch;
- análisis de correlación;
- análisis de asociación entre `RainToday` y `RainTomorrow`;
- generación de una base procesada para continuidad metodológica.

### Productos principales

```text
semana1/data/raw/weatherAUS.csv
semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv
semana1/notebooks/Sumativa1_Rain_Australia_G6.ipynb
semana1/src/estadistica_utils.py
semana1/docs/inventario_outputs_sumativa1.csv
semana1/docs/informe_sumativa1_rain_australia_g6.docx
semana1/docs/informe_sumativa1_rain_australia_g6.pdf
```

### Hallazgos relevantes

- `Humidity3pm` presenta una diferencia importante entre registros con `RainTomorrow = Yes` y `RainTomorrow = No`.
- Se identifican asociaciones relevantes de `RainToday`, `Rainfall`, `Pressure3pm`, `Humidity3pm` y otras variables meteorológicas con la lluvia al día siguiente.
- La matriz de correlación y la auditoría de faltantes constituyen insumos directos para S2 y S3.

---

## 6. Semana 2 - Evaluación Sumativa 2

La Semana 2 valida y profundiza los resultados obtenidos en S1 mediante procedimientos computacionales de remuestreo, simulación y sensibilidad.

### Metodologías principales

- bootstrap no paramétrico;
- intervalos clásicos, percentil y BCa;
- prueba de permutación;
- bootstrap de correlaciones;
- simulación Monte Carlo;
- evaluación de convergencia;
- winsorización 1 % - 99 %;
- diferencia de medianas;
- sensibilidad por exclusión de localidades;
- diagnóstico de outliers;
- consolidación de resultados validados para S3.

### Productos principales

```text
semana2/data/input/weatherAUS_sumativa1_variables_clave.csv
semana2/data/processed/weatherAUS_sumativa2_base_validacion.csv
semana2/data/processed/resultados_validados_sumativa2.csv
semana2/notebooks/Sumativa2_Rain_Australia_G6.ipynb
semana2/src/remuestreo_utils.py
semana2/docs/inventario_outputs_sumativa2.csv
semana2/docs/tables/10_resultados_validados_para_s3.csv
semana2/docs/informe_sumativa2_rain_australia_g6.docx
semana2/docs/informe_sumativa2_rain_australia_g6.pdf
```

### Hallazgos relevantes

- Se confirma la robustez de la diferencia de `Humidity3pm` entre los grupos definidos por `RainTomorrow`.
- Se validan relaciones y parámetros utilizados posteriormente en el modelamiento.
- Se documentan sensibilidad frente a valores extremos, localidad y supuestos estadísticos.
- Se consolida evidencia para seleccionar variables y justificar decisiones en S3.

---

## 7. Semana 3 - Evaluación Sumativa 3

La Semana 3 corresponde al cierre integrado del proyecto y aplica los resultados oficiales de S1 y S2 al manejo de faltantes y al modelamiento predictivo.

### Notebook principal

```text
semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb
```

El notebook contiene:

- **60 celdas totales**;
- **36 celdas de código**;
- **24 celdas Markdown**;
- secuencia de ejecución consecutiva de 1 a 36;
- cero salidas de error almacenadas.

### Metodologías principales

- recuperación trazable de la auditoría de faltantes de S1;
- selección de predictores informada por correlaciones de S1 y estabilidad de S2;
- diez regresiones lineales múltiples explícitas para imputación;
- imputación logística complementaria de `RainToday_bin`;
- comparación entre casos completos, imputación simple e imputación por regresión;
- partición 70 % / 30 % estratificada antes de transformar o seleccionar;
- estandarización estimada exclusivamente con entrenamiento;
- construcción de tres modelos logísticos:
  - M1 informado por S1 y S2;
  - M2 seleccionado mediante procedimiento forward basado en AIC;
  - M3 parsimonioso seleccionado mediante BIC;
- validación cruzada anidada;
- diagnóstico de VIF, linealidad en el logit, residuos e influencia;
- evaluación de suficiencia muestral y separación;
- bootstrap de 10.000 réplicas para coeficientes y odds ratios;
- matrices de confusión, accuracy, precision, recall, F1, ROC-AUC y PR-AUC;
- evaluación de calibración;
- análisis comparativo del impacto de la imputación;
- errores robustos agrupados por `Location`;
- validación temporal y sensibilidades frente a outliers.

### Entregables principales

```text
semana3/data/processed/weatherAUS_sumativa3_modelamiento.csv
semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb
semana3/docs/informe_sumativa3_rain_australia_g6.docx
semana3/docs/informe_sumativa3_rain_australia_g6.pdf
semana3/docs/tables/43_control_metodologico_rubrica.csv
semana3/docs/tables/43a_matriz_respuesta_retroalimentacion_S2.csv
semana3/docs/tables/44_control_integridad_salidas_sumativa3.csv
```

El informe integrado tiene **10 páginas A4** y desarrolla resumen ejecutivo, introducción, metodología integrada, resultados, discusión, conclusiones y recomendaciones, con progresión explícita S1 → S2 → S3.

---

## 8. Resultados finales de Semana 3

- Estrategia de tratamiento de faltantes seleccionada: `imputacion_regresion`.
- Procedimiento logístico seleccionado sin utilizar el conjunto de prueba: `M3_BIC_parsimonioso`.
- Especificación definitiva: `sin_RainToday_bin`.
- VIF máximo de la especificación definitiva: **4,7897**.
- Configuración clasificatoria: ponderación balanceada y umbral OOF de **0,60**.
- Desempeño final en prueba:
  - accuracy: **0,8183**;
  - precision: **0,5831**;
  - recall: **0,6642**;
  - F1: **0,6210**;
  - ROC-AUC: **0,8525**;
  - PR-AUC: **0,6727**.
- Bootstrap: **10.000 de 10.000 réplicas exitosas**.
- Validación temporal:
  - ROC-AUC: **0,8453**;
  - F1: **0,6129**.
- Efectos sensibles al tratamiento de faltantes y a errores robustos por localidad:
  - `MaxTemp`;
  - `MaxTemp_sq`.

Las probabilidades individuales se comunican a partir del modelo no ponderado por su mejor calibración. La configuración balanceada se utiliza para la decisión binaria orientada a incrementar la detección de lluvia.

---

## 9. Integridad de las salidas de Semana 3

La ejecución final contiene:

- **107 archivos CSV** en `semana3/docs/tables/`;
- **24 figuras PNG** en `semana3/docs/figures/`;
- **1 base procesada** en `semana3/data/processed/`;
- **131 artefactos** registrados y verificados mediante SHA-256.

El archivo:

```text
semana3/docs/tables/44_control_integridad_salidas_sumativa3.csv
```

verifica existencia, tamaño y hash SHA-256 de 106 tablas analíticas, 24 figuras y una base procesada. El manifiesto no se incluye a sí mismo para evitar una dependencia circular; por ello, la carpeta `docs/tables/` contiene 107 CSV en total.

---

## 10. Trazabilidad S1 → S2 → S3

```text
Semana 1
├── análisis exploratorio e inferencial
├── auditoría de datos faltantes
├── matriz de correlaciones
└── parámetros iniciales
        │
        ▼
Semana 2
├── bootstrap y permutación
├── simulación Monte Carlo
├── validación de correlaciones
├── análisis de robustez
└── resultados validados para S3
        │
        ▼
Semana 3
├── imputación mediante regresión
├── tres modelos logísticos
├── selección y diagnóstico
├── bootstrap de coeficientes
├── evaluación predictiva
└── comunicación integrada
```

Principales archivos de enlace metodológico:

```text
semana1/docs/tables/03_auditoria_datos_faltantes.csv
semana1/docs/tables/06_matriz_correlacion_pearson.csv
semana2/docs/tables/04b_diagnostico_estabilidad_correlaciones.csv
semana2/docs/tables/08b_diagnostico_outliers_iqr.csv
semana2/docs/tables/10_resultados_validados_para_s3.csv
semana3/docs/tables/01_trazabilidad_S1_S2_hacia_S3.csv
```

---

## 11. Requisitos previos

Se recomienda disponer de:

- Python 3.12.x;
- Git;
- JupyterLab o Jupyter Notebook;
- sistema operativo Windows, Linux o macOS;
- acceso local al repositorio.

Cada carpeta semanal contiene su propio archivo `requirements.txt`.

---

## 12. Instalación

### 12.1 Clonar el repositorio

```bash
git clone https://github.com/edocontreras/mcdia501-estadistica-computacional-g6.git
cd mcdia501-estadistica-computacional-g6
```

### 12.2 Crear un entorno virtual

Desde la raíz:

```bash
python -m venv .venv
```

### 12.3 Activar el entorno

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Linux o macOS:

```bash
source .venv/bin/activate
```

### 12.4 Instalar las dependencias de la semana

Semana 1:

```bash
python -m pip install --upgrade pip
python -m pip install -r semana1/requirements.txt
```

Semana 2:

```bash
python -m pip install --upgrade pip
python -m pip install -r semana2/requirements.txt
```

Semana 3:

```bash
python -m pip install --upgrade pip
python -m pip install -r semana3/requirements.txt
```

### 12.5 Ejecutar JupyterLab

```bash
python -m jupyterlab
```

---

## 13. Orden de ejecución recomendado

Los notebooks deben ejecutarse en orden cronológico:

```text
1. semana1/notebooks/Sumativa1_Rain_Australia_G6.ipynb
2. semana2/notebooks/Sumativa2_Rain_Australia_G6.ipynb
3. semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb
```

En JupyterLab:

```text
Kernel → Restart Kernel and Run All Cells
```

La validación cruzada anidada y el bootstrap de 10.000 réplicas de S3 concentran la mayor parte del tiempo de ejecución.

---

## 14. Reproducibilidad

El proyecto mantiene los siguientes controles:

- semillas explícitas;
- rutas relativas;
- dependencias versionadas;
- separación entre datos crudos, insumos y bases procesadas;
- transformaciones estimadas exclusivamente con entrenamiento en S3;
- conjunto de prueba reservado durante las decisiones propias de modelamiento;
- tablas y figuras exportadas automáticamente;
- controles de integridad mediante tamaño y SHA-256;
- documentación metodológica por semana;
- historial de cambios en `CHANGELOG.md`.

La fuente original del proyecto se conserva en una única ubicación:

```text
semana1/data/raw/weatherAUS.csv
```

S2 y S3 reutilizan este archivo y los productos consolidados de etapas anteriores, evitando copias redundantes.

---

## 15. Alcance interpretativo

Los resultados son predictivos y asociativos; no demuestran relaciones causales.

El conjunto de prueba de S3 se mantuvo reservado durante las decisiones propias de dicha fase. Sin embargo, S1 y S2 analizaron previamente la base completa, por lo que el test no se presenta como una validación externa independiente del proceso exploratorio global.

La dependencia por localidad y tiempo se aborda mediante errores robustos agrupados por `Location`, análisis de sensibilidad y validación temporal. Estos procedimientos no reemplazan una validación externa en nuevas localidades ni un modelo jerárquico espacio-temporal.

---

## 16. Presentación final

La presentación grupal de diez minutos se gestiona mediante el canal de entrega definido en Canvas. El repositorio contiene el notebook, los resultados y los informes que sustentan la exposición, pero el video no se contabiliza como una salida analítica estática.

---

## 17. Control de versiones

Para revisar el estado del repositorio:

```bash
git status
```

Para agregar cambios:

```bash
git add .
```

Para crear un commit:

```bash
git commit -m "docs: consolidar documentación final de la Sumativa 3"
```

Para enviar los cambios:

```bash
git push origin main
```

---

## 18. Archivos que no deben subirse

El archivo `.gitignore` debe excluir al menos:

```gitignore
.venv/
__pycache__/
.ipynb_checkpoints/
*.pyc
.env
logs/
.vscode/
```

No deben incorporarse entornos virtuales, checkpoints locales, cachés, credenciales ni archivos de configuración personal.

---

## 19. Documentación complementaria

- [README de Semana 1](semana1/README.md)
- [README de Semana 2](semana2/README.md)
- [README de Semana 3](semana3/README.md)
- [Historial de cambios](CHANGELOG.md)

---

## 20. Integrantes

- Eduardo Contreras
- Gonzalo Bouldres
- Luis Díaz Giral

**Docente:** Dr. Jean Paul Maidana González  
**Curso:** MCDI501 - Estadística Computacional para la Toma de Decisiones
