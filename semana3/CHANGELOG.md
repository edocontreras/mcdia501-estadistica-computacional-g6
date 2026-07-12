## 2026-07-11 - Integración documental de Semana 3

- Se incorporaron `semana3/docs/informe_sumativa3_rain_australia_g6.docx` y `semana3/docs/informe_sumativa3_rain_australia_g6.pdf`.
- Se actualizó la estructura documental de los README para registrar los informes como productos presentes del repositorio.
- Se documentó explícitamente que `semana3/data/processed/weatherAUS_sumativa3_modelamiento.csv` contiene 142.193 observaciones, 34 columnas y las variables necesarias para reproducir el modelamiento final.
- No se modificaron el notebook, las tablas, las figuras ni la base procesada generada por la ejecución.

# Changelog

## 2026-07-11 — Ejecución integral de Semana 3

- Se ejecutó el notebook completo, con 33 celdas de código en secuencia consecutiva y sin errores.
- Se integraron los resultados efectivos de S1 y S2 en el flujo analítico de S3.
- Se ajustaron diez regresiones lineales múltiples explícitas para imputación y una regresión logística para `RainToday_bin`.
- Se compararon casos completos, imputación simple e imputación por regresión con un alcance común.
- Se ajustaron M1 informado por S1/S2, M2 stepwise AIC y M3 BIC parsimonioso.
- Se completaron la validación anidada, los diagnósticos, el bootstrap de 10.000 réplicas y los análisis de sensibilidad.
- Se generaron 97 tablas, 22 figuras y una base procesada de 142.193 observaciones.
- Se verificaron 119 artefactos computacionales mediante tamaño y SHA-256, sin discrepancias.
- Se actualizaron los README y las dependencias para reflejar exclusivamente la estructura y los archivos realmente presentes en el repositorio.
