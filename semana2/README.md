# Semana 2 - Evaluación Sumativa 2  
## Validación computacional mediante remuestreo, simulación Monte Carlo y análisis de robustez

## 1. Descripción general

La carpeta `semana2` contiene el desarrollo completo de la **Evaluación Sumativa 2** del curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**.

Esta etapa corresponde a una continuación directa de la **Evaluación Sumativa 1**, por lo que no constituye un análisis aislado ni independiente. Su propósito es validar computacionalmente los resultados estadísticos obtenidos previamente, utilizando métodos de remuestreo, prueba de permutación, simulación Monte Carlo y análisis de robustez.

El análisis utiliza el dataset **Rain in Australia** (`weatherAUS`) y mantiene como variable objetivo `RainTomorrow`, la cual indica si lloverá o no al día siguiente. El foco principal de validación se concentra en la variable `Humidity3pm`, debido a que en la Sumativa 1 fue identificada como una de las variables meteorológicas más relevantes para explicar la ocurrencia de lluvia posterior.

La base principal utilizada en esta etapa corresponde al archivo procesado generado en la Sumativa 1:

```text
data/input/weatherAUS_sumativa1_variables_clave.csv
```

A partir de esta base, la Semana 2 profundiza el análisis mediante técnicas computacionales que permiten evaluar la estabilidad, significancia y robustez de los hallazgos iniciales.

---

## 2. Objetivo de la Semana 2

El objetivo de la Semana 2 es **validar, profundizar y evaluar la robustez de los resultados obtenidos en la Sumativa 1 mediante métodos computacionales de simulación y remuestreo**, con el fin de generar insumos estadísticamente respaldados para la etapa posterior de modelamiento predictivo.

De manera específica, la Semana 2 busca:

1. Validar los parámetros principales obtenidos en la Sumativa 1 mediante bootstrap no paramétrico.
2. Estimar intervalos de confianza clásicos, bootstrap percentil y bootstrap BCa.
3. Evaluar la diferencia de `Humidity3pm` entre los grupos `RainTomorrow = Yes` y `RainTomorrow = No`.
4. Contrastar el resultado principal mediante una prueba de permutación.
5. Evaluar la estabilidad de correlaciones entre variables meteorológicas y `RainTomorrow`.
6. Explorar escenarios probabilísticos mediante simulación Monte Carlo.
7. Analizar la robustez del hallazgo principal frente a valores extremos, winsorización, diferencias de medianas y sensibilidad por localidad.
8. Consolidar resultados validados para orientar la Sumativa 3.

---

## 3. Relación con la Sumativa 1

La Semana 2 utiliza como insumo principal la base procesada de la Sumativa 1:

```text
data/input/weatherAUS_sumativa1_variables_clave.csv
```

Esta base contiene las variables meteorológicas seleccionadas y depuradas durante la etapa anterior. La Semana 2 conserva la trazabilidad de ese proceso y mantiene el análisis sobre el mismo fenómeno de estudio: la relación entre condiciones meteorológicas diarias y la ocurrencia de lluvia al día siguiente.

El resultado principal que se valida corresponde a la diferencia de `Humidity3pm` entre los registros con:

```text
RainTomorrow = Yes
RainTomorrow = No
```

Este enfoque permite comprobar si la diferencia observada en la Sumativa 1 se mantiene bajo procedimientos computacionales más exigentes y menos dependientes de supuestos paramétricos.

---

## 4. Estructura de la carpeta

La estructura de la carpeta `semana2` es la siguiente:

```text
semana2/
├── data/
│   ├── input/
│   │   └── weatherAUS_sumativa1_variables_clave.csv
│   │
│   └── processed/
│       ├── weatherAUS_sumativa2_base_validacion.csv
│       └── resultados_validados_sumativa2.csv
│
├── docs/
│   ├── inventario_outputs_sumativa2.csv
│   ├── informe_sumativa2_rain_australia_g6.docx
│   ├── informe_sumativa2_rain_australia_g6.pdf
│   │
│   ├── figures/
│   │   ├── fig_01_bootstrap_media_global_humidity3pm.png
│   │   ├── fig_02_bootstrap_media_humidity3pm_no.png
│   │   ├── fig_03_bootstrap_media_humidity3pm_yes.png
│   │   ├── fig_04_bootstrap_diferencia_medias.png
│   │   ├── fig_05_bootstrap_proporcion_raintomorrow_yes.png
│   │   ├── fig_06_permutacion_diferencia_medias.png
│   │   ├── fig_07_bootstrap_correlaciones.png
│   │   ├── fig_07b_distribuciones_bootstrap_correlaciones.png
│   │   ├── fig_08_montecarlo_distribucion_delta.png
│   │   ├── fig_09_convergencia_montecarlo.png
│   │   └── fig_10_robustez_diferencia_medias.png
│   │
│   └── tables/
│       ├── 00_resumen_base_sumativa2.csv
│       ├── 00b_auditoria_nan_sumativa2.csv
│       ├── 00c_criterio_tratamiento_nan_sumativa2.csv
│       ├── 00d_resumen_casos_validos_por_analisis.csv
│       ├── 00e_configuracion_remuestreo_sumativa2.csv
│       ├── 01_parametros_s1_utilizados.csv
│       ├── 02_bootstrap_parametros_s1.csv
│       ├── 02b_comparacion_intervalos_bootstrap.csv
│       ├── 03_test_permutacion_humidity3pm.csv
│       ├── 04_bootstrap_correlaciones.csv
│       ├── 04b_diagnostico_estabilidad_correlaciones.csv
│       ├── 05_resultados_montecarlo_resumen.csv
│       ├── 06_resultados_montecarlo_umbrales.csv
│       ├── 07_convergencia_montecarlo.csv
│       ├── 08_robustez_outliers_supuestos.csv
│       ├── 09_sensibilidad_por_localidad.csv
│       ├── 09b_sintesis_robustez.csv
│       ├── 10_resultados_validados_para_s3.csv
│       └── 11_control_integridad_salidas_sumativa2.csv
│
├── notebooks/
│   └── Sumativa2_Rain_Australia_G6.ipynb
│
├── src/
│   └── remuestreo_utils.py
│
├── README.md
└── requirements.txt
```

---

## 5. Datos utilizados

### 5.1 Base de entrada

El archivo de entrada principal es:

```text
data/input/weatherAUS_sumativa1_variables_clave.csv
```

Este archivo corresponde a la base procesada en la Sumativa 1. Contiene las variables meteorológicas seleccionadas para continuar el análisis, incluyendo variables numéricas, categóricas, temporales y de localización.

Esta base permite mantener continuidad metodológica entre la Sumativa 1 y la Sumativa 2.

---

### 5.2 Base procesada de validación

La ejecución del notebook genera la siguiente base procesada:

```text
data/processed/weatherAUS_sumativa2_base_validacion.csv
```

Esta base contiene las variables necesarias para los análisis de validación computacional, incluyendo variables derivadas como `RainTomorrow_bin` y `RainToday_bin`.

---

### 5.3 Resultados validados

El archivo consolidado de resultados validados es:

```text
data/processed/resultados_validados_sumativa2.csv
```

Este archivo sintetiza los principales hallazgos de la Semana 2 y constituye un insumo metodológico para la Sumativa 3.

---

## 6. Notebook principal

El análisis completo se encuentra en:

```text
notebooks/Sumativa2_Rain_Australia_G6.ipynb
```

El notebook desarrolla el flujo completo de validación computacional, incluyendo:

1. Carga y verificación de la base proveniente de Sumativa 1.
2. Auditoría de valores faltantes.
3. Definición de casos válidos por análisis.
4. Recuperación de parámetros estimados en Sumativa 1.
5. Bootstrap no paramétrico para parámetros seleccionados.
6. Cálculo de intervalos clásicos, bootstrap percentil y bootstrap BCa.
7. Prueba de permutación para la diferencia de medias de `Humidity3pm`.
8. Evaluación de estabilidad de correlaciones mediante bootstrap.
9. Simulación Monte Carlo basada en parámetros de Sumativa 1.
10. Evaluación de convergencia Monte Carlo.
11. Análisis de robustez frente a outliers, winsorización, medianas y localidad.
12. Generación de resultados validados para Sumativa 3.
13. Generación de tablas, figuras e inventario de salidas.
14. Control de integridad de archivos generados.
15. Conclusión técnica del proceso de validación.

---

## 7. Módulo auxiliar

Las funciones estadísticas reutilizables se encuentran en:

```text
src/remuestreo_utils.py
```

Este módulo contiene funciones para:

- Intervalos de confianza clásicos.
- Bootstrap de medias.
- Bootstrap de proporciones.
- Bootstrap de diferencias de medias.
- Bootstrap de correlaciones.
- Intervalos bootstrap percentil.
- Intervalos bootstrap BCa.
- Jackknife para corrección BCa.
- Prueba de permutación.
- Filtro IQR.
- Winsorización.
- Diferencia de medianas mediante bootstrap.

La separación entre el notebook y el módulo auxiliar permite mantener un flujo de trabajo más limpio, modular, reproducible y reutilizable.

---

## 8. Metodología aplicada

### 8.1 Bootstrap no paramétrico

Se aplican **10.000 remuestras bootstrap** para validar parámetros derivados de la Sumativa 1, incluyendo:

- Media global de `Humidity3pm`.
- Media de `Humidity3pm` para `RainTomorrow = No`.
- Media de `Humidity3pm` para `RainTomorrow = Yes`.
- Diferencia de medias de `Humidity3pm` entre ambos grupos.
- Proporción de `RainTomorrow = Yes`.

Para cada parámetro se calculan:

- Intervalos clásicos.
- Intervalos bootstrap percentil.
- Intervalos bootstrap BCa.

La comparación entre estos enfoques permite evaluar la estabilidad de las estimaciones y reducir la dependencia de un único supuesto inferencial.

---

### 8.2 Prueba de permutación

Se valida la diferencia de medias de `Humidity3pm` entre los grupos `RainTomorrow = Yes` y `RainTomorrow = No` mediante **10.000 permutaciones**.

La hipótesis evaluada es:

```text
H0: La media de Humidity3pm es igual entre días con y sin lluvia al día siguiente.
H1: La media de Humidity3pm es mayor en días con lluvia al día siguiente.
```

Este procedimiento permite contrastar el resultado principal sin depender exclusivamente de los supuestos paramétricos de la prueba t de Welch.

---

### 8.3 Estabilidad de correlaciones

Se evalúan cinco correlaciones relevantes con `RainTomorrow_bin` mediante intervalos bootstrap al 95 %:

- `Humidity3pm`.
- `RainToday_bin`.
- `Rainfall`.
- `Pressure3pm`.
- `MaxTemp`.

Este análisis permite identificar qué asociaciones mantienen dirección estable y cuáles deben ser tratadas con mayor cautela en la etapa predictiva.

---

### 8.4 Simulación Monte Carlo

Se ejecuta una simulación Monte Carlo con **100.000 iteraciones**, utilizando parámetros estimados en la Sumativa 1.

La simulación permite explorar escenarios de humedad y evaluar umbrales de `Humidity3pm` asociados a la ocurrencia de lluvia al día siguiente.

Este análisis tiene carácter exploratorio, por lo que no reemplaza un modelo predictivo formal. Su finalidad es apoyar la interpretación probabilística de los resultados y entregar antecedentes para la etapa posterior de modelamiento.

---

### 8.5 Convergencia Monte Carlo

Se evalúa la convergencia de la simulación Monte Carlo para verificar la estabilidad de los resultados simulados a medida que aumenta el número de iteraciones.

Este control permite comprobar que los resultados no dependen de una cantidad insuficiente de simulaciones y que la estimación final es estable.

---

### 8.6 Análisis de robustez

Se evalúa la sensibilidad del resultado principal frente a:

- Filtro IQR por grupo.
- Winsorización 1 %-99 %.
- Diferencia de medianas mediante bootstrap.
- Exclusión individual de localidades.

Este análisis permite verificar si la diferencia de `Humidity3pm` entre grupos se mantiene ante cambios en el tratamiento de valores extremos, supuestos estadísticos y composición espacial de la muestra.

---

## 9. Resultados principales validados

La Semana 2 valida que `Humidity3pm` presenta una diferencia robusta entre los registros con `RainTomorrow = Yes` y `RainTomorrow = No`.

El resultado principal corresponde a:

```text
Media Humidity3pm cuando RainTomorrow = Yes: mayor que en RainTomorrow = No.
Diferencia de Humidity3pm entre grupos: positiva, estable y estadísticamente significativa.
```

La diferencia observada se mantiene bajo:

- Intervalos clásicos.
- Bootstrap percentil.
- Bootstrap BCa.
- Prueba de permutación.
- Análisis de robustez frente a outliers.
- Winsorización.
- Diferencia de medianas.
- Sensibilidad por localidad.

En consecuencia, `Humidity3pm` se consolida como la variable meteorológica prioritaria para la etapa posterior de modelamiento predictivo.

---

## 10. Resultados validados para la Sumativa 3

Los resultados principales validados para la Sumativa 3 son los siguientes:

### 10.1 `Humidity3pm` como predictor prioritario

`Humidity3pm` presenta la mayor asociación con `RainTomorrow_bin` y una diferencia robusta entre días con y sin lluvia al día siguiente.

Por esta razón, debe ser considerada como una variable prioritaria en la etapa de modelamiento predictivo.

---

### 10.2 `RainToday_bin` como variable antecedente relevante

`RainToday_bin` mantiene una correlación positiva y estable con `RainTomorrow_bin`.

Esto indica que la ocurrencia de lluvia el día actual constituye un antecedente relevante para estudiar la probabilidad de lluvia al día siguiente.

---

### 10.3 `Rainfall` como variable meteorológica candidata

`Rainfall` presenta una asociación positiva con `RainTomorrow_bin`.

Sin embargo, debe tratarse con cautela debido a su posible asimetría, presencia de valores bajos o nulos y concentración de registros sin precipitación.

---

### 10.4 `Pressure3pm` como variable complementaria

`Pressure3pm` presenta una asociación negativa estable con `RainTomorrow_bin`.

Este resultado es coherente con el comportamiento meteorológico esperado, ya que condiciones de menor presión atmosférica suelen asociarse con mayor inestabilidad atmosférica.

---

### 10.5 `MaxTemp` como variable complementaria de menor magnitud

`MaxTemp` presenta una asociación negativa estable, aunque con menor fuerza relativa frente a `Humidity3pm`, `RainToday_bin`, `Rainfall` y `Pressure3pm`.

Por ello, puede considerarse como variable complementaria, pero no como predictor principal.

---

### 10.6 Control de localidad para modelamiento posterior

La sensibilidad por exclusión de localidades muestra que el resultado principal no depende exclusivamente de una estación meteorológica específica.

Sin embargo, `Location` debe considerarse en la etapa predictiva, ya sea como:

- Variable categórica.
- Agrupación territorial.
- Criterio de validación espacial.
- Variable de control para evaluar estabilidad del modelo.

---

## 11. Tratamiento de valores faltantes

En la Semana 2 se utiliza el criterio de **casos válidos por análisis**. No se aplica imputación, debido a que el objetivo principal es validar los resultados obtenidos en la Sumativa 1 sin introducir supuestos adicionales sobre los datos faltantes.

Esta decisión es metodológicamente adecuada para una etapa de validación inferencial y computacional.

La imputación debe incorporarse en la Sumativa 3 dentro del flujo predictivo. Cualquier imputador, transformación o escalamiento deberá ajustarse únicamente sobre los datos de entrenamiento, evitando fuga de información hacia los conjuntos de validación o prueba.

---

## 12. Salidas generadas

La ejecución del notebook genera las siguientes salidas:

- Bases procesadas en `data/processed/`.
- Tablas en `docs/tables/`.
- Figuras en `docs/figures/`.
- Inventario de salidas en `docs/inventario_outputs_sumativa2.csv`.
- Control de integridad en `docs/tables/11_control_integridad_salidas_sumativa2.csv`.

El control de integridad permite verificar que las salidas analíticas esperadas fueron generadas correctamente.

---

## 13. Tablas generadas

Las tablas generadas por el notebook se almacenan en:

```text
docs/tables/
```

Las tablas disponibles son:

```text
00_resumen_base_sumativa2.csv
00b_auditoria_nan_sumativa2.csv
00c_criterio_tratamiento_nan_sumativa2.csv
00d_resumen_casos_validos_por_analisis.csv
00e_configuracion_remuestreo_sumativa2.csv
01_parametros_s1_utilizados.csv
02_bootstrap_parametros_s1.csv
02b_comparacion_intervalos_bootstrap.csv
03_test_permutacion_humidity3pm.csv
04_bootstrap_correlaciones.csv
04b_diagnostico_estabilidad_correlaciones.csv
05_resultados_montecarlo_resumen.csv
06_resultados_montecarlo_umbrales.csv
07_convergencia_montecarlo.csv
08_robustez_outliers_supuestos.csv
09_sensibilidad_por_localidad.csv
09b_sintesis_robustez.csv
10_resultados_validados_para_s3.csv
11_control_integridad_salidas_sumativa2.csv
```

Estas tablas permiten revisar, reproducir y respaldar los principales resultados estadísticos de la Semana 2.

---

## 14. Figuras generadas

Las figuras generadas por el notebook se almacenan en:

```text
docs/figures/
```

Las figuras disponibles son:

```text
fig_01_bootstrap_media_global_humidity3pm.png
fig_02_bootstrap_media_humidity3pm_no.png
fig_03_bootstrap_media_humidity3pm_yes.png
fig_04_bootstrap_diferencia_medias.png
fig_05_bootstrap_proporcion_raintomorrow_yes.png
fig_06_permutacion_diferencia_medias.png
fig_07_bootstrap_correlaciones.png
fig_07b_distribuciones_bootstrap_correlaciones.png
fig_08_montecarlo_distribucion_delta.png
fig_09_convergencia_montecarlo.png
fig_10_robustez_diferencia_medias.png
```

Estas figuras complementan la interpretación visual de los resultados obtenidos en el notebook.

---

## 15. Inventario de outputs

El inventario de salidas de la Semana 2 se encuentra en:

```text
docs/inventario_outputs_sumativa2.csv
```

Este archivo permite mantener trazabilidad sobre las salidas generadas por el notebook, indicando el tipo de archivo, su ubicación y su función dentro del análisis.

---

## 16. Control de integridad

El control de integridad se encuentra en:

```text
docs/tables/11_control_integridad_salidas_sumativa2.csv
```

Este archivo verifica la existencia de las principales salidas analíticas esperadas de la Semana 2.

Su propósito es asegurar que el repositorio contenga todos los archivos necesarios para reproducir, revisar y respaldar los resultados generados por el notebook.

Los informes finales en formato Word y PDF no forman parte del control de integridad automático, ya que corresponden a documentos de entrega elaborados a partir de las salidas analíticas.

---

## 17. Informe técnico de la Sumativa 2

Los informes finales de la Sumativa 2 deben incorporarse en la carpeta:

```text
docs/
```

Los archivos esperados son:

```text
docs/informe_sumativa2_rain_australia_g6.docx
docs/informe_sumativa2_rain_australia_g6.pdf
```

El archivo `.docx` corresponde a la versión editable del informe técnico.  
El archivo `.pdf` corresponde a la versión final de entrega.

Ambos documentos deben elaborarse a partir de:

- El notebook principal.
- Las tablas generadas en `docs/tables/`.
- Las figuras generadas en `docs/figures/`.
- El inventario de outputs.
- El archivo de resultados validados para la Sumativa 3.
- El control de integridad de salidas.

El informe técnico debe sintetizar:

1. Contexto del problema.
2. Relación con la Sumativa 1.
3. Datos utilizados.
4. Tratamiento de valores faltantes.
5. Metodología de remuestreo.
6. Resultados bootstrap.
7. Prueba de permutación.
8. Bootstrap de correlaciones.
9. Simulación Monte Carlo.
10. Análisis de robustez.
11. Resultados validados para la Sumativa 3.
12. Conclusiones técnicas.

---

## 18. Cómo ejecutar la Semana 2

Desde la raíz del repositorio, ingresar a la carpeta de Semana 2:

```bash
cd semana2
```

Crear un entorno virtual:

```bash
python -m venv .venv
```

Activar el entorno virtual en Windows PowerShell:

```bash
.venv\Scripts\Activate.ps1
```

Actualizar `pip`:

```bash
python -m pip install --upgrade pip
```

Instalar dependencias:

```bash
python -m pip install -r requirements.txt
```

Registrar el kernel de Jupyter:

```bash
python -m ipykernel install --user --name mcdi501-g6 --display-name "Python 3.12 - MCDI501 G6"
```

Abrir JupyterLab:

```bash
jupyter lab
```

Luego abrir y ejecutar el notebook:

```text
notebooks/Sumativa2_Rain_Australia_G6.ipynb
```

Para reproducir completamente los resultados, se debe ejecutar:

```text
Kernel → Restart Kernel and Run All Cells
```

Al finalizar la ejecución, el notebook genera o actualiza:

```text
data/processed/
docs/tables/
docs/figures/
docs/inventario_outputs_sumativa2.csv
docs/tables/11_control_integridad_salidas_sumativa2.csv
```

---

## 19. Dependencias principales

Las dependencias necesarias se encuentran en:

```text
requirements.txt
```

Las principales librerías utilizadas son:

- `numpy`
- `pandas`
- `scipy`
- `matplotlib`
- `jupyterlab`
- `ipykernel`

---

## 20. Consideraciones para la Sumativa 3

La Sumativa 3 debe utilizar los resultados validados de la Semana 2 como insumo metodológico.

En particular, se recomienda:

1. Priorizar `Humidity3pm` como variable predictora principal.
2. Incluir `RainToday_bin`, `Rainfall` y `Pressure3pm` como variables candidatas.
3. Considerar `MaxTemp` como variable complementaria.
4. Evaluar el rol de `Location` en el diseño predictivo.
5. Definir un tratamiento formal de valores faltantes dentro del flujo de modelamiento.
6. Separar adecuadamente los datos en entrenamiento, validación y prueba.
7. Evitar fuga de información al aplicar imputación, transformación o escalamiento.
8. Evaluar métricas de desempeño predictivo apropiadas para una variable binaria.

---

## 21. Conclusión técnica

La Semana 2 confirma que `Humidity3pm` presenta una diferencia robusta entre los registros con lluvia al día siguiente y los registros sin lluvia posterior.

El resultado principal se mantiene bajo distintos enfoques de validación computacional, incluyendo bootstrap, intervalos clásicos, intervalos bootstrap percentil, intervalos bootstrap BCa, prueba de permutación, simulación Monte Carlo y análisis de robustez.

La evidencia obtenida respalda que `Humidity3pm` debe mantenerse como variable prioritaria para la Sumativa 3. Además, variables como `RainToday_bin`, `Rainfall`, `Pressure3pm` y `MaxTemp` pueden ser consideradas como variables complementarias en la etapa posterior de modelamiento predictivo.

La Semana 2 queda documentada como una etapa metodológicamente trazable, computacionalmente reproducible y estadísticamente coherente con los resultados obtenidos en la Sumativa 1.
