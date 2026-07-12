## [2026-07-12] - Consolidación documental y verificación final de Semana 3

### Añadido

- Se incorporaron los informes técnicos definitivos de la Evaluación Sumativa 3:
  - `semana3/docs/informe_sumativa3_rain_australia_g6.docx`
  - `semana3/docs/informe_sumativa3_rain_australia_g6.pdf`
- Se incorporó la base procesada final:
  - `semana3/data/processed/weatherAUS_sumativa3_modelamiento.csv`
- Se documentó que la base procesada contiene:
  - 142.193 observaciones;
  - 34 columnas;
  - 99.535 registros de entrenamiento;
  - 42.658 registros de prueba;
  - las variables imputadas, transformadas y codificadas necesarias para reproducir el modelamiento final.
- Se incorporó el manifiesto final de integridad:
  - `semana3/docs/tables/44_control_integridad_salidas_sumativa3.csv`

### Cambiado

- Se actualizaron el `README.md` principal y `semana3/README.md` para reflejar el estado final de las tres evaluaciones sumativas.
- Se corrigieron las referencias documentales para declarar los informes Word y PDF como productos presentes del repositorio.
- Se actualizaron los conteos de salidas de Semana 3 a:
  - 107 archivos CSV en `semana3/docs/tables/`;
  - 24 figuras PNG en `semana3/docs/figures/`;
  - 131 artefactos verificados mediante tamaño y SHA-256.
- Se actualizó el número de celdas de código ejecutadas del notebook a 36.
- Se normalizó la documentación de `semana3/requirements.txt` manteniendo las versiones utilizadas en el entorno validado.

### Corregido

- Se reemplazaron las cifras preliminares de 33 celdas, 97 tablas, 22 figuras y 119 artefactos por los valores finales verificados.
- Se eliminaron referencias que indicaban que la Semana 3 se encontraba pendiente o en preparación.
- Se corrigieron rutas, nombres de archivos y descripciones para mantener coherencia entre notebook, README, CHANGELOG, tablas, figuras, base procesada e informes.
- Se eliminaron copias redundantes de productos pertenecientes a la Semana 2 desde `semana3/data/processed/`.
- Se eliminó el directorio local `.ipynb_checkpoints/` del paquete final.

### Verificación final

- Notebook de Semana 3:
  - 60 celdas totales;
  - 36 celdas de código;
  - 24 celdas Markdown;
  - ejecuciones consecutivas de 1 a 36;
  - cero errores almacenados.
- Salidas computacionales:
  - 107 archivos CSV;
  - 24 figuras PNG;
  - 1 base procesada;
  - 131 artefactos verificados mediante SHA-256;
  - cero archivos faltantes;
  - cero discrepancias de tamaño;
  - cero discrepancias de hash.
- Informe integrado:
  - formato Word y PDF;
  - 10 páginas A4;
  - contenido alineado con los resultados del notebook;
  - progresión explícita S1 → S2 → S3.
- No se modificaron el código, las salidas almacenadas, las tablas, las figuras ni la base procesada generada por la ejecución final validada.

## [2026-07-11] - Ejecución integral de Semana 3

### Añadido

- Se ejecutó completamente el notebook:
  - `semana3/notebooks/Sumativa3_Rain_Australia_G6.ipynb`
- Se integraron los resultados efectivos de las Sumativas 1 y 2 en el flujo analítico de la Sumativa 3.
- Se ajustaron diez modelos de regresión lineal múltiple para la imputación de variables numéricas.
- Se utilizó regresión logística para el tratamiento de `RainToday_bin`.
- Se compararon sistemáticamente tres estrategias de tratamiento de datos faltantes:
  - casos completos;
  - imputación simple;
  - imputación mediante regresión.
- Se ajustaron los tres modelos logísticos solicitados:
  - M1 informado por S1 y S2;
  - M2 seleccionado mediante procedimiento forward basado en AIC;
  - M3 parsimonioso seleccionado mediante BIC.
- Se completaron:
  - validación cruzada anidada;
  - diagnóstico de multicolinealidad;
  - linealidad en el logit;
  - análisis de residuos e influencia;
  - suficiencia muestral y separación;
  - bootstrap de 10.000 réplicas;
  - evaluación predictiva;
  - calibración;
  - análisis comparativo de imputación;
  - sensibilidad por `Location`;
  - validación temporal.
- Se generó la base procesada final con 142.193 observaciones y 34 columnas.

### Resultados principales

- Estrategia de imputación seleccionada: `imputacion_regresion`.
- Modelo seleccionado: `M3_BIC_parsimonioso`.
- Especificación definitiva: `sin_RainToday_bin`.
- VIF máximo definitivo: 4,7897.
- Configuración clasificatoria: balanceada, con umbral OOF de 0,60.
- Desempeño en prueba:
  - accuracy: 0,8183;
  - precision: 0,5831;
  - recall: 0,6642;
  - F1: 0,6210;
  - ROC-AUC: 0,8525;
  - PR-AUC: 0,6727.
- Bootstrap:
  - 10.000 de 10.000 réplicas exitosas.
- Validación temporal:
  - ROC-AUC: 0,8453;
  - F1: 0,6129.
- Los términos `MaxTemp` y `MaxTemp_sq` fueron identificados como sensibles al tratamiento de faltantes y a la dependencia por localidad.
