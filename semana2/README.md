# Semana 2 - Evaluación Sumativa 2

## MCDI501 - Estadística Computacional para la Toma de Decisiones

## Descripción de la Semana 2

La Semana 2 corresponde a la validación computacional de los resultados obtenidos en la Evaluación Sumativa 1, utilizando métodos de remuestreo, prueba de permutación, simulación Monte Carlo y análisis de robustez.

Esta etapa no constituye un análisis independiente, sino una continuación directa de la Sumativa 1. Por ello, utiliza como insumo principal la base procesada generada en la etapa anterior:

```text
data/input/weatherAUS_sumativa1_variables_clave.csv
```

El análisis utiliza el dataset **Rain in Australia** (`weatherAUS`) y se centra en la variable objetivo `RainTomorrow`, que indica si lloverá o no al día siguiente. El resultado principal validado corresponde a la diferencia de `Humidity3pm` entre los registros con `RainTomorrow = Yes` y `RainTomorrow = No`.

## Objetivo de la Semana 2

Validar, profundizar y evaluar la robustez de los resultados obtenidos en la Sumativa 1 mediante métodos computacionales de simulación y remuestreo, con el fin de generar insumos estadísticamente respaldados para la etapa posterior de modelamiento predictivo.

## Estructura de la carpeta

```text
semana2/
├── data/
│   ├── input/
│   │   └── weatherAUS_sumativa1_variables_clave.csv
│   └── processed/
│       ├── weatherAUS_sumativa2_base_validacion.csv
│       └── resultados_validados_sumativa2.csv
├── docs/
│   ├── inventario_outputs_sumativa2.csv
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
├── notebooks/
│   └── Sumativa2_Rain_Australia_G6.ipynb
├── src/
│   └── remuestreo_utils.py
├── README.md
└── requirements.txt
```

Los informes finales de la Sumativa 2 se incorporan posteriormente en la carpeta `docs/`:

```text
docs/informe_sumativa2_rain_australia_g6.docx
docs/informe_sumativa2_rain_australia_g6.pdf
```

Estos documentos se elaboran a partir de las tablas, figuras y resultados validados generados por el notebook. No forman parte del control de integridad automático, ya que dicho control verifica únicamente las salidas analíticas generadas por código.

## Datos utilizados

La entrada principal de Semana 2 es:

```text
data/input/weatherAUS_sumativa1_variables_clave.csv
```

Este archivo corresponde a la base procesada de la Sumativa 1 y contiene las variables meteorológicas seleccionadas para continuar el análisis.

La ejecución del notebook genera la base de validación de Semana 2:

```text
data/processed/weatherAUS_sumativa2_base_validacion.csv
```

También genera el archivo consolidado de resultados validados:

```text
data/processed/resultados_validados_sumativa2.csv
```

Este último archivo constituye la entrada metodológica para la Sumativa 3.

## Notebook principal

El análisis completo se encuentra en:

```text
notebooks/Sumativa2_Rain_Australia_G6.ipynb
```

El notebook desarrolla el flujo completo de validación computacional:

1. Carga y verificación de la base proveniente de Sumativa 1.
2. Auditoría de valores faltantes y definición de casos válidos por análisis.
3. Recuperación de parámetros estimados en Sumativa 1.
4. Bootstrap no paramétrico para parámetros seleccionados.
5. Cálculo de intervalos clásicos, bootstrap percentil y bootstrap BCa.
6. Prueba de permutación para la diferencia de medias de `Humidity3pm`.
7. Evaluación de estabilidad de correlaciones mediante bootstrap.
8. Simulación Monte Carlo basada en parámetros de Sumativa 1.
9. Evaluación de convergencia Monte Carlo.
10. Análisis de robustez frente a outliers, winsorización, medianas y localidad.
11. Generación de resultados validados para Sumativa 3.
12. Control de integridad de salidas generadas.

## Módulo auxiliar

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

La separación entre el notebook y el módulo auxiliar permite mantener un flujo de trabajo ordenado, reproducible y reutilizable.

## Cómo ejecutar la Semana 2

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

## Dependencias principales

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

## Metodología aplicada

### Bootstrap no paramétrico

Se aplican 10.000 remuestras bootstrap para validar parámetros derivados de la Sumativa 1, incluyendo:

- Media global de `Humidity3pm`.
- Media de `Humidity3pm` para `RainTomorrow = No`.
- Media de `Humidity3pm` para `RainTomorrow = Yes`.
- Diferencia de medias de `Humidity3pm` entre ambos grupos.
- Proporción de `RainTomorrow = Yes`.

Para cada parámetro se calculan intervalos clásicos, intervalos bootstrap percentil e intervalos bootstrap BCa.

### Prueba de permutación

Se valida la diferencia de medias de `Humidity3pm` entre los grupos `RainTomorrow = Yes` y `RainTomorrow = No` mediante 10.000 permutaciones. Este procedimiento permite contrastar el resultado principal sin depender exclusivamente de los supuestos paramétricos de la prueba t de Welch.

### Estabilidad de correlaciones

Se evalúan cinco correlaciones relevantes con `RainTomorrow_bin` mediante intervalos bootstrap al 95 %:

- `Humidity3pm`
- `RainToday_bin`
- `Rainfall`
- `Pressure3pm`
- `MaxTemp`

El análisis permite identificar qué asociaciones mantienen dirección estable y cuáles podrían requerir cautela en la etapa predictiva.

### Simulación Monte Carlo

Se ejecuta una simulación Monte Carlo con 100.000 iteraciones, utilizando parámetros estimados en la Sumativa 1. La simulación permite explorar escenarios de humedad y evaluar umbrales de `Humidity3pm` asociados a la ocurrencia de lluvia al día siguiente.

### Análisis de robustez

Se evalúa la sensibilidad del resultado principal frente a:

- Filtro IQR por grupo.
- Winsorización 1 %-99 %.
- Diferencia de medianas mediante bootstrap.
- Exclusión individual de localidades.

Este análisis permite verificar si la diferencia de `Humidity3pm` entre grupos se mantiene ante cambios en el tratamiento de valores extremos, supuestos estadísticos y composición espacial de la muestra.

## Resultados validados para modelamiento posterior

La Semana 2 valida que `Humidity3pm` presenta una diferencia robusta entre los registros con `RainTomorrow = Yes` y `RainTomorrow = No`. Esta diferencia se mantiene bajo intervalos clásicos, bootstrap percentil, bootstrap BCa, prueba de permutación y análisis de robustez.

Los resultados principales validados para la Sumativa 3 son:

1. **`Humidity3pm` como predictor prioritario**  
   Presenta la mayor asociación con `RainTomorrow_bin` y una diferencia robusta entre días con y sin lluvia al día siguiente.

2. **`RainToday_bin` como variable antecedente relevante**  
   Mantiene correlación positiva y estable con `RainTomorrow_bin`.

3. **`Rainfall` como variable meteorológica candidata**  
   Presenta asociación positiva con `RainTomorrow_bin`, aunque debe tratarse con cautela por su posible asimetría y concentración de valores bajos o nulos.

4. **`Pressure3pm` como variable complementaria**  
   Presenta asociación negativa estable con `RainTomorrow_bin`, coherente con el comportamiento meteorológico esperado.

5. **`MaxTemp` como variable complementaria de menor magnitud**  
   Presenta asociación negativa estable, aunque con menor fuerza relativa frente a `Humidity3pm`, `RainToday_bin`, `Rainfall` y `Pressure3pm`.

6. **Robustez del hallazgo principal**  
   La diferencia de `Humidity3pm` entre grupos se mantiene al aplicar filtro IQR, winsorización, diferencia de medianas y sensibilidad por localidad.

7. **Control de localidad para modelamiento posterior**  
   La sensibilidad por exclusión de localidades muestra que el resultado principal no depende exclusivamente de una estación meteorológica específica. Sin embargo, `Location` debe considerarse en la etapa predictiva, ya sea como variable categórica, agrupación territorial o criterio de validación.

El archivo que consolida estos resultados es:

```text
data/processed/resultados_validados_sumativa2.csv
```

## Tratamiento de valores faltantes

En Semana 2 se utiliza el criterio de casos válidos por análisis. No se aplica imputación, porque el objetivo es validar los resultados obtenidos en Sumativa 1 sin introducir supuestos adicionales sobre los datos faltantes.

La imputación debe incorporarse en la Sumativa 3 dentro del flujo predictivo. Cualquier imputador, transformación o escalamiento deberá ajustarse únicamente sobre los datos de entrenamiento, evitando fuga de información hacia validación o prueba.

## Salidas generadas

La ejecución del notebook genera las siguientes salidas:

- Bases procesadas en `data/processed/`.
- Tablas en `docs/tables/`.
- Figuras en `docs/figures/`.
- Inventario de salidas en `docs/inventario_outputs_sumativa2.csv`.
- Control de integridad en `docs/tables/11_control_integridad_salidas_sumativa2.csv`.

El control de integridad permite verificar que las salidas analíticas esperadas fueron generadas correctamente.

## Consideraciones para Sumativa 3

La Sumativa 3 debe utilizar los resultados validados de Semana 2 como insumo metodológico. En particular, se recomienda:

- Priorizar `Humidity3pm` como variable predictora principal.
- Incluir `RainToday_bin`, `Rainfall` y `Pressure3pm` como variables candidatas.
- Considerar `MaxTemp` como variable complementaria.
- Evaluar el rol de `Location` en el diseño predictivo.
- Definir un tratamiento formal de valores faltantes dentro del flujo de modelamiento.
- Separar adecuadamente los datos en entrenamiento, validación y prueba.
- Evitar fuga de información al aplicar imputación, transformación o escalamiento.
- Evaluar métricas de desempeño predictivo apropiadas para una variable binaria.
