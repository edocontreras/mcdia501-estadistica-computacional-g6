# Semana 3 - Evaluación Sumativa 3

## Modelamiento predictivo integrado de `RainTomorrow`

**Curso:** MCDI501 - Estadística Computacional para la Toma de Decisiones  
**Grupo:** 6  
**Integrantes:** Eduardo Contreras; Gonzalo Bouldres; Luis Díaz Giral  
**Docente:** Dr. Jean Paul Maidana González  
**Semilla reproducible:** `5012026`

---

## 1. Descripción general

La Semana 3 integra los resultados obtenidos en las Sumativas 1 y 2 para construir y evaluar modelos de regresión logística destinados a predecir `RainTomorrow`. El flujo comprende manejo de datos faltantes, comparación de estrategias de imputación, selección de variables, diagnóstico de modelos, evaluación predictiva, bootstrap y análisis de sensibilidad.

El notebook fue ejecutado completamente, con 33 celdas de código en secuencia consecutiva y sin errores de ejecución.

---

## 2. Trazabilidad S1 → S2 → S3

La progresión metodológica se sustenta en:

- auditoría y porcentajes de datos faltantes obtenidos en S1;
- matriz de correlaciones construida en S1;
- relaciones priorizadas y evaluadas mediante remuestreo en S2;
- diagnóstico de outliers y análisis de robustez de S2;
- parámetros y resultados exportados por ambas fases.

S3 no modifica los resultados de S1 o S2. Las decisiones nuevas se estiman exclusivamente con el conjunto de entrenamiento o se presentan como análisis complementarios propios de S3.

---

## 3. Estructura de Semana 3

```text
semana3/
├── data/
│   ├── raw/
│   │   └── .gitkeep
│   └── processed/
│       └── weatherAUS_sumativa3_modelamiento.csv
├── docs/
│   ├── figures/
│   ├── tables/
│   ├── informe_sumativa3_rain_australia_g6.docx
│   └── informe_sumativa3_rain_australia_g6.pdf
├── notebooks/
│   └── Sumativa3_Rain_Australia_G6.ipynb
├── README.md
├── requirements.txt
├── LICENSE
├── .gitignore
└── data/.gitkeep
```

La carpeta `data/raw/` permanece vacía porque Semana 3 no incorpora una fuente de datos nueva. El notebook utiliza el dataset original de S1 y las evidencias generadas en S1 y S2.

---

## 4. Datos utilizados

### 4.1 Insumos

```text
semana1/data/raw/weatherAUS.csv
semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv
semana1/docs/tables/
semana2/data/processed/
semana2/docs/tables/
```

### 4.2 Base procesada

```text
semana3/data/processed/weatherAUS_sumativa3_modelamiento.csv
```

Características verificadas:

- 142.193 observaciones;
- 34 columnas;
- 99.535 registros de entrenamiento;
- 42.658 registros de prueba;
- cero filas duplicadas;
- cero identificadores `row_id` duplicados;
- cero faltantes en las variables utilizadas por los modelos;
- prevalencia de `RainTomorrow = Yes` de 22,418 % en entrenamiento y prueba.

La base conserva algunas variables auxiliares excluidas del modelamiento, por lo que estas pueden mantener valores faltantes sin afectar el pipeline final. El archivo no está vacío: contiene la partición `train/test`, las variables imputadas utilizadas por el modelo, las variables estacionales codificadas, `Rainfall_log1p` y los identificadores necesarios para reproducir el análisis.

---

## 5. Manejo de datos faltantes

S1 identificó dieciséis variables numéricas continuas con valores faltantes. Diez de ellas forman parte de la matriz de correlaciones entregada en S1 y constituyen el conjunto analítico de S3:

```text
MinTemp, MaxTemp, Rainfall, WindGustSpeed,
Humidity9am, Humidity3pm, Pressure9am, Pressure3pm,
Temp9am, Temp3pm
```

Para cada variable se ajustó una regresión lineal múltiple explícita con tres a cinco predictores de la matriz de S1. `RainToday_bin` se imputó mediante regresión logística y `RainTomorrow` no se imputó.

Las variables `Evaporation`, `Sunshine`, `WindSpeed9am`, `WindSpeed3pm`, `Cloud9am` y `Cloud3pm` fueron contabilizadas y excluidas antes de la imputación y del modelamiento porque no forman parte de la matriz correlacional de S1 ni de la validación de S2. La decisión queda documentada en las tablas `03b` y `03f`.

Se compararon tres estrategias con alcance común:

1. casos completos;
2. imputación simple con parámetros estimados en entrenamiento;
3. imputación secuencial determinística mediante regresiones explícitas.

---

## 6. Modelamiento y validación

### 6.1 Preparación

- división estratificada 70/30 antes de imputar, escalar o seleccionar;
- transformación `log1p` y corrección de retransmisión para `Rainfall`;
- tratamiento conservador de outliers y sensibilidad mediante winsorización;
- estandarización ajustada únicamente con entrenamiento;
- codificación dummy de `Season`, con `Summer` como referencia;
- exclusión justificada de categóricas de alta cardinalidad del modelo principal.

### 6.2 Modelos logísticos

- **M1 S1/S2:** especificación guiada por evidencia previa;
- **M2 stepwise AIC:** selección forward por bloques con regla de parada;
- **M3 BIC parsimonioso:** búsqueda exhaustiva de subconjuntos.

La selección inferencial utiliza `statsmodels.Logit` sin ponderación. La evaluación clasificatoria compara configuraciones no ponderadas y balanceadas.

### 6.3 Diagnóstico y estabilidad

Se evaluaron:

- VIF;
- linealidad en el logit mediante Box-Tidwell;
- residuos de devianza;
- leverage y distancia de Cook;
- suficiencia muestral y separación;
- errores robustos agrupados por `Location`;
- bootstrap no paramétrico de 10.000 réplicas.

### 6.4 Sensibilidades

Se analizaron:

- las tres estrategias de imputación;
- winsorización;
- ponderación de clases y umbral;
- incorporación de `Location`;
- validación temporal;
- observaciones influyentes.

---

## 7. Resultados principales

- Estrategia seleccionada: `imputacion_regresion`.
- Modelo inferencial: `M3_BIC_parsimonioso`.
- Especificación definitiva: `sin_RainToday_bin`.
- VIF máximo definitivo: 4,7897.
- Configuración clasificatoria: balanceada, con umbral OOF 0,60.
- Prueba: accuracy 0,8183; precision 0,5831; recall 0,6642; F1 0,6210; ROC-AUC 0,8525; PR-AUC 0,6727.
- Bootstrap: 10.000 de 10.000 réplicas exitosas.
- Parámetros inestables bajo bootstrap fila a fila: cero.
- Efectos sensibles a errores robustos por `Location`: `MaxTemp` y `MaxTemp_sq`.
- Efectos cuya conclusión cambia entre imputaciones: `MaxTemp` y `MaxTemp_sq`.
- Validación temporal: ROC-AUC 0,8453 y F1 0,6129.

Las probabilidades interpretables proceden del modelo inferencial sin ponderación, que presenta mejor calibración. La configuración balanceada se utiliza para la clasificación y su umbral operativo.

---

## 8. Salidas generadas por el notebook

La ejecución produjo:

- 97 tablas CSV en `docs/tables/`;
- 22 figuras PNG en `docs/figures/`;
- una base procesada en `data/processed/`;
- el notebook ejecutado y guardado.

Las tablas se organizan por bloque:

| Rango | Contenido |
|---|---|
| `00`–`12b` | entorno, trazabilidad, faltantes e imputación |
| `13`–`23b` | preparación, selección y evaluación de modelos |
| `24`–`30b` | diagnóstico, calibración, multicolinealidad e influencia |
| `31a`–`32b` | bootstrap y estabilidad |
| `33`–`41b` | impacto de imputación y sensibilidades |
| `42`–`44` | síntesis y controles finales |

Las tablas de advertencias `08c`, `15b`, `20d` y `31b` contienen sus encabezados y cero registros porque no se produjeron incidencias en esos procedimientos.

---

## 9. Control de integridad

```text
semana3/docs/tables/44_control_integridad_salidas_sumativa3.csv
```

El control registra 119 artefactos computacionales:

- 96 tablas adicionales al propio control;
- 22 figuras;
- una base procesada.

El control metodológico de cobertura se encuentra en:

```text
semana3/docs/tables/43_control_metodologico_rubrica.csv
```

---

## 10. Informe integrado

Los productos documentales de Semana 3 se encuentran en:

```text
semana3/docs/informe_sumativa3_rain_australia_g6.docx
semana3/docs/informe_sumativa3_rain_australia_g6.pdf
```

El informe consolida la trazabilidad S1-S2-S3, la comparación de estrategias de imputación, los tres modelos logísticos, los diagnósticos, el bootstrap, el análisis de sensibilidad y las conclusiones técnicas.

---

## 11. Ejecución

Desde la raíz del repositorio:

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
Kernel → Restart Kernel and Run All Cells
```

La validación anidada y el bootstrap de 10.000 réplicas concentran la mayor parte del tiempo de ejecución.

---

## 12. Dependencias principales

| Componente | Versión validada |
|---|---:|
| Python | 3.12.4 |
| NumPy | 1.26.4 |
| pandas | 2.2.2 |
| SciPy | 1.13.1 |
| scikit-learn | 1.4.2 |
| statsmodels | 0.14.2 |
| Matplotlib | 3.8.4 |

El detalle completo se encuentra en `requirements.txt`.

---

## 13. Alcance interpretativo

Los resultados son predictivos y asociativos; no permiten establecer causalidad. La dependencia espacial y temporal se examina mediante errores robustos por localidad, desempeño por `Location` y validación temporal.

La estabilidad bootstrap corresponde al modelo y al pipeline seleccionados. Los efectos asociados a `MaxTemp` deben interpretarse con cautela porque presentan sensibilidad tanto a la dependencia por localidad como al tratamiento de datos faltantes.
