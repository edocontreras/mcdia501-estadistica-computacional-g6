# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

El formato está basado en [Keep a Changelog](https://keepachangelog.com/es/1.1.0/).

---

## [2026-07-03] - Actualización Semana 2: Evaluación Sumativa 2

### Añadido

- Desarrollo completo de la carpeta `semana2/` correspondiente a la **Evaluación Sumativa 2** del curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**.

- Notebook principal de Semana 2:

```text
semana2/notebooks/Sumativa2_Rain_Australia_G6.ipynb
```

- Base de entrada de Semana 2 proveniente de la Sumativa 1:

```text
semana2/data/input/weatherAUS_sumativa1_variables_clave.csv
```

- Bases procesadas generadas por la Sumativa 2:

```text
semana2/data/processed/weatherAUS_sumativa2_base_validacion.csv
semana2/data/processed/resultados_validados_sumativa2.csv
```

- Módulo auxiliar de funciones estadísticas reutilizables:

```text
semana2/src/remuestreo_utils.py
```

- Tablas de resultados generadas por el notebook en:

```text
semana2/docs/tables/
```

- Figuras de resultados generadas por el notebook en:

```text
semana2/docs/figures/
```

- Inventario de salidas de la Sumativa 2:

```text
semana2/docs/inventario_outputs_sumativa2.csv
```

- Control de integridad de salidas analíticas:

```text
semana2/docs/tables/11_control_integridad_salidas_sumativa2.csv
```

- Archivo `requirements.txt` específico para Semana 2, con dependencias necesarias para ejecutar el notebook.

---

### Metodologías incorporadas

- Bootstrap no paramétrico para validación de parámetros principales.
- Intervalos de confianza clásicos.
- Intervalos bootstrap percentil.
- Intervalos bootstrap BCa.
- Prueba de permutación para diferencia de medias.
- Bootstrap de correlaciones.
- Simulación Monte Carlo.
- Evaluación de convergencia Monte Carlo.
- Análisis de robustez frente a valores extremos.
- Winsorización 1 % - 99 %.
- Diferencia de medianas mediante bootstrap.
- Sensibilidad por exclusión individual de localidades.
- Consolidación de resultados validados para la Sumativa 3.

---

### Resultados principales documentados

- Validación de la diferencia de `Humidity3pm` entre registros con `RainTomorrow = Yes` y `RainTomorrow = No`.
- Confirmación de que `Humidity3pm` presenta una diferencia robusta, estable y estadísticamente significativa entre ambos grupos.
- Identificación de `Humidity3pm` como variable prioritaria para la etapa posterior de modelamiento predictivo.
- Identificación de `RainToday_bin`, `Rainfall` y `Pressure3pm` como variables complementarias principales para la etapa posterior.
- Evaluación de `MaxTemp` como variable exploratoria de apoyo dentro del análisis de correlaciones, sin incorporarla como insumo prioritario en el consolidado final de resultados validados.
- Confirmación de que el resultado principal no depende exclusivamente de una localidad meteorológica específica.

---

### Documentación actualizada

- Actualización completa del archivo:

```text
semana2/README.md
```

- El README de Semana 2 incorpora:
  - Descripción general de la Evaluación Sumativa 2.
  - Objetivos de la etapa.
  - Relación metodológica con la Sumativa 1.
  - Estructura completa de carpetas.
  - Datos utilizados.
  - Notebook principal.
  - Módulo auxiliar.
  - Metodología aplicada.
  - Resultados principales.
  - Tablas generadas.
  - Figuras generadas.
  - Inventario de outputs.
  - Control de integridad.
  - Tratamiento de valores faltantes.
  - Consideraciones para la Sumativa 3.
  - Sección para incorporar el informe técnico en formato Word y PDF.
  - Aclaración del alcance exploratorio de `MaxTemp`.

---

### Pendiente

- Incorporar en `semana2/docs/` los informes finales de la Sumativa 2:

```text
semana2/docs/informe_sumativa2_rain_australia_g6.docx
semana2/docs/informe_sumativa2_rain_australia_g6.pdf
```

- Actualizar el `README.md` principal del repositorio para reflejar que Semana 2 ya se encuentra desarrollada.
- Mantener `semana3/` como carpeta preparada para la etapa posterior de modelamiento predictivo.

---

## [2026-06-28] - Actualización Semana 1: Evaluación Sumativa 1

### Añadido

- Desarrollo de la carpeta `semana1/` correspondiente a la **Evaluación Sumativa 1**.
- Dataset original `weatherAUS.csv` incorporado en:

```text
semana1/data/raw/weatherAUS.csv
```

- Base procesada con variables clave para continuidad del proyecto:

```text
semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv
```

- Notebook principal de Semana 1:

```text
semana1/notebooks/Sumativa1_Rain_Australia_G6.ipynb
```

- Tablas de resultados generadas por la Sumativa 1 en:

```text
semana1/docs/tables/
```

- Figuras generadas por la Sumativa 1 en:

```text
semana1/docs/figures/
```

- Inventario de outputs de Semana 1.
- Documentación interna de Semana 1 mediante:

```text
semana1/README.md
```

---

### Metodologías incorporadas

- Carga y revisión inicial del dataset `Rain in Australia`.
- Análisis exploratorio de datos.
- Auditoría de valores faltantes.
- Selección de variables meteorológicas relevantes.
- Estadística descriptiva.
- Comparación de `Humidity3pm` entre grupos definidos por `RainTomorrow`.
- Análisis de correlación entre variables meteorológicas y lluvia al día siguiente.
- Prueba t de Welch para comparación de medias.
- Generación de tablas, figuras y base procesada para continuidad hacia Semana 2.

---

### Resultados principales documentados

- Identificación de `Humidity3pm` como una variable relevante para explicar diferencias entre días con y sin lluvia al día siguiente.
- Evidencia de que los registros con `RainTomorrow = Yes` presentan mayor humedad relativa a las 3 pm que los registros con `RainTomorrow = No`.
- Generación de una base procesada que sirve como insumo directo para la Sumativa 2.
- Consolidación de resultados exploratorios e inferenciales iniciales.

---

### Cambiado

- Se reemplaza el enfoque inicial de repositorio vacío por una estructura funcional con datos, notebooks, tablas, figuras y documentación.
- Se establece continuidad metodológica entre Semana 1 y Semana 2 mediante el archivo:

```text
semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv
```

- Se actualiza la documentación interna de Semana 1 para describir el uso del dataset, la estructura del análisis y los productos generados.

---

## [2026-06-26] - Creación inicial del repositorio

### Añadido

- Repositorio inicial del proyecto grupal asociado al curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**.
- Estructura incremental del proyecto con carpetas semanales:

```text
semana1/
semana2/
semana3/
```

- README principal en la raíz del repositorio con:
  - Descripción general del proyecto.
  - Referencia al dataset `Rain in Australia` (`weatherAUS.csv`).
  - Objetivo inicial del análisis.
  - Estructura esperada del proyecto.
  - Requisitos de instalación.
  - Uso de Jupyter Notebook/JupyterLab.
  - Control de versiones y reproducibilidad.

- Archivo `.gitignore` en la raíz para excluir:
  - Entornos virtuales.
  - Caché de Python.
  - Checkpoints de Jupyter.
  - Archivos `.env`.
  - Logs.
  - Configuraciones locales de editor.

- En cada carpeta semanal se incorporó una estructura base con:
  - `data/`
  - `data/raw/` o `data/input/`, según corresponda.
  - `data/processed/`
  - `docs/`
  - `notebooks/`
  - `src/`
  - `README.md`
  - `requirements.txt`

- Repositorio Git inicializado con rama principal `main`.

---

### Pendiente en esta etapa inicial

- Desarrollar los notebooks analíticos de cada semana.
- Incorporar resultados procesados.
- Generar tablas y figuras.
- Completar documentación específica de cada semana.
- Incorporar informes técnicos de entrega.
- Preparar la etapa de modelamiento predictivo en Semana 3.

---

## Estado actual del proyecto

### Semana 1

Estado: **desarrollada y documentada**.

Incluye dataset original, base procesada, notebook, tablas, figuras, inventario de salidas y documentación específica.

---

### Semana 2

Estado: **desarrollada analíticamente y documentada**.

Incluye base de entrada, base procesada, notebook, funciones auxiliares, tablas, figuras, inventario, control de integridad y README actualizado.

Pendiente específico: incorporar informe técnico final en formato Word y PDF dentro de `semana2/docs/`.

---

### Semana 3

Estado: **preparada para desarrollo posterior**.

Debe utilizar los resultados validados de Semana 2 como insumo para la etapa de modelamiento predictivo.
