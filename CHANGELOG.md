# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

El formato se basa en Keep a Changelog y el proyecto utiliza versionado cronológico por fecha de consolidación.

## [2026-07-12] - Consolidación final de la Semana 3: Evaluación Sumativa 3

### Añadido

- Desarrollo completo de la carpeta `semana3/`, correspondiente a la Evaluación Sumativa 3 del curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**.
- Notebook maestro ejecutado y documentado:
  - `semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb`
- Base procesada final:
  - `semana3/data/processed/weatherAUS_sumativa3_modelado.csv`
- Informe técnico final en los dos formatos exigidos:
  - `semana3/docs/informe_sumativa3_rain_australia_g6.docx`
  - `semana3/docs/informe_sumativa3_rain_australia_g6.pdf`
- Tablas analíticas generadas por el notebook en:
  - `semana3/docs/tables/`
- Figuras analíticas generadas por el notebook en:
  - `semana3/docs/figures/`
- Manifiesto de integridad SHA-256 para las salidas computacionales de la Semana 3.
- Archivo `requirements.txt` específico para la Semana 3, con versiones reproducibles de las dependencias utilizadas.
- Documentación completa de la Semana 3 mediante:
  - `semana3/README.md`

### Metodologías incorporadas

- Integración metodológica explícita de los resultados de S1 → S2 → S3.
- Recuperación del análisis de datos faltantes efectuado en la Sumativa 1.
- Selección de predictores para imputación a partir de correlaciones identificadas en S1 y validadas en S2.
- Imputación mediante regresión lineal múltiple.
- Comparación sistemática de tres estrategias de tratamiento de faltantes:
  - casos completos;
  - imputación simple;
  - imputación mediante regresión.
- Verificación de supuestos de los modelos lineales de imputación:
  - R² y R² ajustado;
  - validación cruzada;
  - RMSE y MAE;
  - normalidad de residuos;
  - heterocedasticidad;
  - especificación funcional;
  - multicolinealidad;
  - independencia y autocorrelación.
- División estratificada de entrenamiento y prueba en proporción 70 % / 30 %.
- Tratamiento de outliers informado por los resultados de S1 y S2.
- Estandarización de variables numéricas y codificación de variables categóricas.
- Construcción de tres modelos de regresión logística:
  - M1 informado por S1 y S2;
  - M2 seleccionado mediante procedimiento forward basado en AIC;
  - M3 parsimonioso seleccionado mediante BIC.
- Interpretación de coeficientes y odds ratios.
- Selección del modelo sin utilizar anticipadamente el conjunto de prueba.
- Validación cruzada anidada de cinco pliegues.
- Diagnósticos del modelo final:
  - VIF;
  - linealidad en el logit;
  - residuos;
  - leverage;
  - distancia de Cook;
  - observaciones influyentes;
  - eventos por parámetro;
  - separación completa y cuasi completa.
- Bootstrap de 10.000 réplicas para:
  - coeficientes;
  - odds ratios;
  - intervalos de confianza al 95 %;
  - comparación con intervalos tradicionales.
- Evaluación predictiva mediante:
  - matrices de confusión;
  - accuracy;
  - precision;
  - recall;
  - F1-score;
  - ROC-AUC;
  - PR-AUC;
  - Brier score;
  - calibración.
- Comparación simétrica del impacto de las tres estrategias de imputación utilizando una especificación común y un conjunto de prueba común.
- Análisis de sensibilidad mediante:
  - errores robustos agrupados por `Location`;
  - partición temporal;
  - evaluación del efecto de observaciones influyentes;
  - comparación de configuraciones balanceadas y no balanceadas.

### Resultados principales documentados

- Conservación de la trazabilidad entre los hallazgos exploratorios e inferenciales de S1, la validación por remuestreo de S2 y el modelamiento predictivo de S3.
- Confirmación de `Humidity3pm` como una de las variables más relevantes para la clasificación de `RainTomorrow`.
- Construcción y comparación de los tres modelos logísticos exigidos.
- Selección de un modelo parsimonioso basado en BIC, con desempeño discriminativo equivalente a alternativas más complejas.
- Ejecución exitosa de 10.000 réplicas bootstrap para evaluar estabilidad de coeficientes y odds ratios.
- Comparación explícita del impacto de la imputación sobre:
  - tamaño muestral;
  - coeficientes;
  - intervalos de confianza;
  - accuracy;
  - F1;
  - ROC-AUC;
  - estabilidad de las conclusiones.
- Identificación de `MaxTemp` y `MaxTemp²` como términos sensibles a la estrategia de tratamiento de datos faltantes.
- Selección de la imputación por regresión por su capacidad de conservar la muestra analítica y preservar la estructura multivariada, sin afirmar diferencias predictivas materialmente relevantes frente a las otras estrategias.
- Incorporación de recomendaciones técnicas orientadas a la toma de decisiones y a la interpretación responsable del modelo.

### Cambiado

- Se actualizó el `README.md` principal para reflejar el estado final de las tres sumativas.
- Se actualizó `semana3/README.md` para documentar:
  - objetivos;
  - insumos;
  - estructura;
  - metodología;
  - resultados;
  - reproducibilidad;
  - inventario de productos;
  - trazabilidad S1 → S2 → S3.
- Se actualizó `semana3/requirements.txt` con las versiones utilizadas en el entorno de ejecución.
- Se normalizó la nomenclatura de los informes de Semana 3:
  - `informe_sumativa3_rain_australia_g6.docx`
  - `informe_sumativa3_rain_australia_g6.pdf`
- Se corrigió la denominación metodológica de la evaluación de cinco pliegues a **validación cruzada anidada**, evitando confundirla con una validación externa independiente.
- Se actualizó la documentación general para declarar únicamente productos efectivamente existentes en el repositorio.
- Se verificó que los informes finales de la Semana 2 ya se encuentran incorporados en:
  - `semana2/docs/informe_sumativa2_rain_australia_g6.docx`
  - `semana2/docs/informe_sumativa2_rain_australia_g6.pdf`

### Corregido

- Se corrigieron cifras desactualizadas de la Semana 3 que indicaban 97 tablas, 22 figuras y 119 artefactos.
- Los conteos finales verificados son:
  - **107 archivos CSV** en `semana3/docs/tables/`;
  - **24 figuras PNG** en `semana3/docs/figures/`;
  - **131 artefactos** registrados y verificados mediante SHA-256.
- Se corrigió el número de celdas de código ejecutadas del notebook:
  - valor anterior: 33;
  - valor final verificado: **36**.
- Se eliminaron contradicciones entre el README principal, el README de Semana 3, el CHANGELOG y el inventario real de salidas.
- Se corrigieron referencias de rutas y nombres de archivos para evitar enlaces rotos en GitHub.
- Se ajustó el informe final para mantener coherencia terminológica, numérica y metodológica con el notebook ejecutado y sus salidas.

### Eliminado

- Se eliminó del paquete final el directorio local:
  - `semana3/notebooks/.ipynb_checkpoints/`
- No se eliminaron ni modificaron el notebook principal, las tablas, las figuras ni la base procesada generada por la ejecución validada.

### Verificación final

- Notebook de Semana 3:
  - 60 celdas totales;
  - 36 celdas de código;
  - 24 celdas Markdown;
  - secuencia de ejecución consecutiva de 1 a 36;
  - cero salidas de error almacenadas.
- Salidas computacionales:
  - 107 archivos CSV;
  - 24 figuras PNG;
  - 1 base procesada;
  - 131 artefactos verificados mediante SHA-256;
  - cero archivos faltantes;
  - cero discrepancias de tamaño;
  - cero discrepancias de hash.
- Informe final:
  - Word y PDF incorporados;
  - 10 páginas A4;
  - coherencia visual entre Word y PDF;
  - ausencia de páginas vacías, desbordes y solapamientos.
- Integridad del análisis:
  - no se reejecutó ni modificó el notebook durante la actualización documental;
  - no se alteraron las tablas, figuras ni datos procesados generados por la ejecución validada.

## [2026-07-11] - Ejecución integral de la Semana 3

### Añadido

- Integración efectiva de los resultados de S1 y S2 en el flujo analítico de S3.
- Ajuste de diez regresiones lineales múltiples explícitas para imputación.
- Ajuste complementario de una regresión logística para `RainToday_bin`.
- Comparación entre casos completos, imputación simple e imputación por regresión bajo un alcance analítico común.
- Ajuste de:
  - M1 informado por S1/S2;
  - M2 forward mediante AIC;
  - M3 parsimonioso mediante BIC.
- Validación cruzada anidada, diagnósticos, bootstrap y análisis de sensibilidad.
- Generación de la base procesada final con 142.193 observaciones y 34 columnas.

## [2026-07-03] - Actualización Semana 2: Evaluación Sumativa 2

### Añadido

- Desarrollo completo de la carpeta `semana2/`, correspondiente a la Evaluación Sumativa 2 del curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**.
- Notebook principal de Semana 2:
  - `semana2/notebooks/Sumativa2_Rain_Australia_G6.ipynb`
- Base de entrada de Semana 2 proveniente de la Sumativa 1:
  - `semana2/data/input/weatherAUS_sumativa1_variables_clave.csv`
- Bases procesadas generadas por la Sumativa 2:
  - `semana2/data/processed/weatherAUS_sumativa2_base_validacion.csv`
  - `semana2/data/processed/resultados_validados_sumativa2.csv`
- Módulo auxiliar de funciones estadísticas reutilizables:
  - `semana2/src/remuestreo_utils.py`
- Tablas de resultados generadas por el notebook en:
  - `semana2/docs/tables/`
- Figuras de resultados generadas por el notebook en:
  - `semana2/docs/figures/`
- Inventario de salidas de la Sumativa 2:
  - `semana2/docs/inventario_outputs_sumativa2.csv`
- Control de integridad de salidas analíticas:
  - `semana2/docs/tables/11_control_integridad_salidas_sumativa2.csv`
- Archivo `requirements.txt` específico para Semana 2, con las dependencias necesarias para ejecutar el notebook.

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

### Resultados principales documentados

- Validación de la diferencia de `Humidity3pm` entre registros con `RainTomorrow = Yes` y `RainTomorrow = No`.
- Confirmación de que `Humidity3pm` presenta una diferencia robusta, estable y estadísticamente significativa entre ambos grupos.
- Identificación de `Humidity3pm` como variable prioritaria para la etapa posterior de modelamiento predictivo.
- Identificación de `RainToday_bin`, `Rainfall` y `Pressure3pm` como variables complementarias principales.
- Evaluación de `MaxTemp` como variable exploratoria de apoyo dentro del análisis de correlaciones, sin incorporarla como insumo prioritario en el consolidado inicial de resultados validados.
- Confirmación de que el resultado principal no depende exclusivamente de una localidad meteorológica específica.

### Documentación actualizada

- Actualización completa de:
  - `semana2/README.md`
- El README de Semana 2 incorpora:
  - descripción general de la evaluación;
  - objetivos;
  - relación metodológica con la Sumativa 1;
  - estructura de carpetas;
  - datos utilizados;
  - notebook principal;
  - módulo auxiliar;
  - metodología;
  - resultados;
  - tablas;
  - figuras;
  - inventario de outputs;
  - control de integridad;
  - tratamiento de valores faltantes;
  - consideraciones para la Sumativa 3;
  - informes técnicos en Word y PDF;
  - aclaración del alcance exploratorio de `MaxTemp`.

### Resuelto posteriormente

- Los informes finales de la Sumativa 2 fueron incorporados en:
  - `semana2/docs/informe_sumativa2_rain_australia_g6.docx`
  - `semana2/docs/informe_sumativa2_rain_australia_g6.pdf`
- El README principal fue actualizado para reflejar que la Semana 2 se encuentra desarrollada y documentada.
- La carpeta `semana3/` fue desarrollada y consolidada como etapa de modelamiento predictivo.

## [2026-06-28] - Actualización Semana 1: Evaluación Sumativa 1

### Añadido

- Desarrollo de la carpeta `semana1/`, correspondiente a la Evaluación Sumativa 1.
- Dataset original `weatherAUS.csv` incorporado en:
  - `semana1/data/raw/weatherAUS.csv`
- Base procesada con variables clave para la continuidad del proyecto:
  - `semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv`
- Notebook principal de Semana 1:
  - `semana1/notebooks/Sumativa1_Rain_Australia_G6.ipynb`
- Tablas de resultados generadas por la Sumativa 1 en:
  - `semana1/docs/tables/`
- Figuras generadas por la Sumativa 1 en:
  - `semana1/docs/figures/`
- Inventario de outputs de Semana 1.
- Documentación interna mediante:
  - `semana1/README.md`

### Metodologías incorporadas

- Carga y revisión inicial del dataset **Rain in Australia**.
- Análisis exploratorio de datos.
- Auditoría de valores faltantes.
- Selección de variables meteorológicas relevantes.
- Estadística descriptiva.
- Comparación de `Humidity3pm` entre grupos definidos por `RainTomorrow`.
- Análisis de correlación entre variables meteorológicas y lluvia al día siguiente.
- Prueba t de Welch para comparación de medias.
- Generación de tablas, figuras y base procesada para continuidad hacia Semana 2.

### Resultados principales documentados

- Identificación de `Humidity3pm` como variable relevante para explicar diferencias entre días con y sin lluvia al día siguiente.
- Evidencia de que los registros con `RainTomorrow = Yes` presentan mayor humedad relativa a las 3 pm que los registros con `RainTomorrow = No`.
- Generación de una base procesada utilizada como insumo directo para la Sumativa 2.
- Consolidación de resultados exploratorios e inferenciales iniciales.

### Cambiado

- Se reemplazó el enfoque inicial de repositorio vacío por una estructura funcional con datos, notebooks, tablas, figuras y documentación.
- Se estableció continuidad metodológica entre Semana 1 y Semana 2 mediante:
  - `semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv`
- Se actualizó la documentación interna de Semana 1 para describir el uso del dataset, la estructura del análisis y los productos generados.

## [2026-06-26] - Creación inicial del repositorio

### Añadido

- Repositorio inicial del proyecto grupal asociado al curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**.
- Estructura incremental del proyecto:
  - `semana1/`
  - `semana2/`
  - `semana3/`
- README principal en la raíz del repositorio con:
  - descripción general;
  - referencia al dataset **Rain in Australia** (`weatherAUS.csv`);
  - objetivo inicial;
  - estructura esperada;
  - requisitos de instalación;
  - uso de Jupyter Notebook/JupyterLab;
  - control de versiones;
  - reproducibilidad.
- Archivo `.gitignore` para excluir:
  - entornos virtuales;
  - caché de Python;
  - checkpoints de Jupyter;
  - archivos `.env`;
  - logs;
  - configuraciones locales de editor.
- Estructura base por semana:
  - `data/`;
  - `data/raw/` o `data/input/`;
  - `data/processed/`;
  - `docs/`;
  - `notebooks/`;
  - `src/`;
  - `README.md`;
  - `requirements.txt`.
- Repositorio Git inicializado con rama principal `main`.

### Estado inicial

- Desarrollo pendiente de los notebooks analíticos.
- Incorporación pendiente de resultados procesados.
- Generación pendiente de tablas y figuras.
- Documentación específica pendiente.
- Informes técnicos pendientes.
- Etapa de modelamiento predictivo de Semana 3 pendiente.

## Estado actual del proyecto

### Semana 1

**Estado:** desarrollada, ejecutada y documentada.

Incluye dataset original, base procesada, notebook, tablas, figuras, inventario de salidas y documentación específica.

### Semana 2

**Estado:** desarrollada, ejecutada y documentada.

Incluye base de entrada, bases procesadas, notebook, funciones auxiliares, tablas, figuras, inventario, control de integridad, README e informes técnicos en Word y PDF.

### Semana 3

**Estado:** finalizada, ejecutada, verificada y documentada.

Incluye notebook maestro, base procesada, 107 archivos CSV, 24 figuras PNG, manifiesto SHA-256 con 131 artefactos verificados, informe técnico en Word y PDF, README y dependencias reproducibles.

La presentación de diez minutos se gestiona como producto de exposición y entrega en Canvas; no se contabiliza como una salida analítica estática del repositorio.
