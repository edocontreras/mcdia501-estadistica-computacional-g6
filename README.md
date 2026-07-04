# MCDI501 - Estadística Computacional para la Toma de Decisiones

## Descripción del proyecto

Este repositorio contiene el desarrollo incremental del proyecto grupal asociado al curso **MCDI501 - Estadística Computacional para la Toma de Decisiones**.

El proyecto utiliza el dataset **Rain in Australia** (`weatherAUS`), el cual contiene aproximadamente 10 años de observaciones meteorológicas diarias registradas en distintas estaciones climáticas de Australia. El objetivo general del análisis es estudiar variables meteorológicas relevantes y evaluar su relación con la ocurrencia de lluvia al día siguiente, representada por la variable objetivo `RainTomorrow`.

El trabajo se organiza por semanas, manteniendo trazabilidad entre datos originales, datos procesados, notebooks, funciones auxiliares, tablas, figuras, informes técnicos e insumos para etapas posteriores. La **Semana 1** desarrolla el análisis exploratorio, descriptivo e inferencial inicial; la **Semana 2** valida y profundiza esos resultados mediante métodos computacionales de remuestreo, simulación Monte Carlo y análisis de robustez; y la **Semana 3** queda preparada para la fase posterior de modelamiento, consolidación y comunicación final del proyecto.

El repositorio está diseñado para favorecer la reproducibilidad computacional, la documentación metodológica, el control de versiones mediante GitHub y la continuidad entre las distintas evaluaciones del curso.

---

## Estructura general del repositorio

```text
mcdia500-estadistica-computacional-g6/
│
├── semana1/
│   ├── data/
│   │   ├── raw/
│   │   └── processed/
│   ├── docs/
│   │   ├── figures/
│   │   └── tables/
│   ├── notebooks/
│   ├── src/
│   ├── README.md
│   ├── LICENSE
│   └── requirements.txt
│
├── semana2/
│   ├── data/
│   │   ├── raw/
│   │   ├── input/
│   │   └── processed/
│   ├── docs/
│   │   ├── figures/
│   │   └── tables/
│   ├── notebooks/
│   ├── src/
│   ├── README.md
│   ├── LICENSE
│   └── requirements.txt
│
├── semana3/
│   ├── data/
│   ├── docs/
│   ├── notebooks/
│   ├── src/
│   ├── README.md
│   ├── LICENSE
│   └── requirements.txt
│
├── README.md
├── CHANGELOG.md
└── .gitignore
```

---

## Descripción de carpetas

Cada carpeta semanal mantiene una estructura orientada a asegurar orden, trazabilidad y reproducibilidad.

* `data/raw/`: contiene los datos originales o crudos del proyecto.
* `data/input/`: contiene datos provenientes de una etapa anterior y utilizados como entrada metodológica de una nueva fase.
* `data/processed/`: contiene datasets procesados, depurados, transformados o consolidados.
* `docs/`: contiene documentación complementaria, inventarios, informes técnicos, tablas y figuras.
* `docs/figures/`: contiene gráficos y visualizaciones exportadas desde los notebooks.
* `docs/tables/`: contiene tablas de resultados generadas durante el análisis.
* `notebooks/`: contiene los notebooks principales de análisis, validación, simulación o modelamiento.
* `src/`: contiene funciones reutilizables, módulos auxiliares y código Python del proyecto.
* `requirements.txt`: contiene las dependencias necesarias para reproducir cada entrega semanal.

---

## Avance por semana

### Semana 1 - Evaluación Sumativa 1

La Semana 1 desarrolla la primera etapa analítica del proyecto. Incluye limpieza inicial, análisis exploratorio, estadística descriptiva, inferencia estadística, pruebas de hipótesis, análisis de asociación y generación de resultados base para las siguientes etapas.

El foco principal de esta etapa es estudiar el comportamiento de variables meteorológicas relevantes y su relación con `RainTomorrow`, identificando especialmente el rol de variables como `Humidity3pm`, `RainToday`, `Rainfall`, `Pressure3pm` y `MaxTemp`.

Productos principales de Semana 1:

```text
semana1/
├── data/
│   ├── raw/
│   │   └── weatherAUS.csv
│   └── processed/
│       └── weatherAUS_sumativa1_variables_clave.csv
│
├── docs/
│   ├── figures/
│   ├── tables/
│   ├── inventario_outputs_sumativa1.csv
│   ├── informe_sumativa1_rain_australia_g6.docx
│   └── informe_sumativa1_rain_australia_g6.pdf
│
├── notebooks/
│   └── Sumativa1_Rain_Australia_G6.ipynb
│
├── src/
│   └── estadistica_utils.py
│
├── README.md
├── LICENSE
└── requirements.txt
```

La Semana 1 contiene:

* 1 dataset original en `data/raw/`.
* 1 dataset procesado en `data/processed/`.
* 1 notebook principal en `notebooks/Sumativa1_Rain_Australia_G6.ipynb`.
* 1 módulo auxiliar en `src/estadistica_utils.py`.
* Tablas de resultados exportadas en `docs/tables/`.
* Figuras exportadas en `docs/figures/`.
* 1 inventario de salidas en `docs/inventario_outputs_sumativa1.csv`.
* 1 informe técnico en formato Word.
* 1 informe técnico en formato PDF.

---

### Semana 2 - Evaluación Sumativa 2

La Semana 2 corresponde a la validación computacional de los resultados obtenidos en la Semana 1. Esta etapa no constituye un análisis independiente, sino una continuación directa de la Sumativa 1.

El objetivo de la Semana 2 es validar, profundizar y evaluar la robustez de los resultados estadísticos obtenidos previamente, mediante técnicas de simulación y remuestreo. Para ello, se utilizan métodos como bootstrap no paramétrico, intervalos bootstrap percentil y BCa, prueba de permutación, bootstrap de correlaciones, simulación Monte Carlo y análisis de sensibilidad frente a outliers y supuestos estadísticos.

La base principal utilizada en Semana 2 proviene directamente de la Semana 1:

```text
semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv
```

y se incorpora como archivo de entrada en:

```text
semana2/data/input/weatherAUS_sumativa1_variables_clave.csv
```

Productos principales de Semana 2:

```text
semana2/
├── data/
│   ├── input/
│   │   └── weatherAUS_sumativa1_variables_clave.csv
│   └── processed/
│       ├── weatherAUS_sumativa2_base_validacion.csv
│       └── resultados_validados_sumativa2.csv
│
├── docs/
│   ├── figures/
│   ├── tables/
│   ├── inventario_outputs_sumativa2.csv
│   ├── informe_sumativa2_rain_australia_g6.docx
│   └── informe_sumativa2_rain_australia_g6.pdf
│
├── notebooks/
│   └── Sumativa2_Rain_Australia_G6.ipynb
│
├── src/
│   └── remuestreo_utils.py
│
├── README.md
├── LICENSE
└── requirements.txt
```

La Semana 2 contiene:

* 1 dataset de entrada proveniente de la Sumativa 1.
* 1 dataset procesado para validación computacional.
* 1 archivo consolidado de resultados validados para la Sumativa 3.
* 1 notebook principal en `notebooks/Sumativa2_Rain_Australia_G6.ipynb`.
* 1 módulo auxiliar en `src/remuestreo_utils.py`.
* Tablas de resultados exportadas en `docs/tables/`.
* Figuras exportadas en `docs/figures/`.
* 1 inventario de salidas en `docs/inventario_outputs_sumativa2.csv`.
* 1 informe técnico en formato Word.
* 1 informe técnico en formato PDF.

El informe técnico de Semana 2 documenta los resultados obtenidos mediante bootstrap no paramétrico, intervalos percentil y BCa, prueba de permutación, estabilidad de correlaciones, simulación Monte Carlo, análisis de robustez y recomendaciones metodológicas para la Sumativa 3.

---

### Semana 3 - Preparación para Evaluación Sumativa 3

La Semana 3 se mantiene preparada para la fase posterior del proyecto. Esta etapa utiliza como insumo directo los resultados validados de la Semana 2, especialmente:

* Parámetros robustamente estimados.
* Correlaciones estables.
* Variables meteorológicas con mayor respaldo estadístico.
* Observaciones influyentes o sensibles.
* Recomendaciones metodológicas derivadas del análisis de robustez.
* Archivo consolidado `resultados_validados_sumativa2.csv`.

La Semana 3 se orienta al desarrollo de la siguiente fase analítica, asociada a modelamiento predictivo, consolidación de resultados, comunicación técnica y cierre del proyecto.

---

## Trazabilidad metodológica entre Semana 1 y Semana 2

La continuidad entre Semana 1 y Semana 2 es un aspecto central del proyecto.

La Semana 1 genera los resultados estadísticos iniciales:

* Estadística descriptiva de variables meteorológicas.
* Intervalos de confianza clásicos.
* Pruebas de hipótesis paramétricas.
* Matriz de correlación de Pearson.
* Análisis de asociación entre `RainToday` y `RainTomorrow`.
* Identificación de variables relevantes para explicar la lluvia al día siguiente.

La Semana 2 utiliza estos resultados como base para aplicar métodos computacionales de validación:

* Bootstrap no paramétrico para validar intervalos de confianza.
* Intervalos bootstrap percentil y BCa.
* Prueba de permutación para validar la prueba t de Welch.
* Bootstrap de correlaciones para evaluar estabilidad.
* Simulación Monte Carlo basada en parámetros estimados en la Semana 1.
* Análisis de robustez frente a outliers, winsorización, medianas y sensibilidad por localidad.
* Consolidación de resultados validados para la Sumativa 3.

La relación principal entre ambas etapas puede resumirse de la siguiente manera:

```text
Semana 1
│
├── Base procesada:
│   └── weatherAUS_sumativa1_variables_clave.csv
│
├── Resultados inferenciales:
│   ├── intervalos de confianza
│   ├── prueba t de Welch
│   ├── matriz de correlación
│   └── proporciones asociadas a RainTomorrow
│
▼
Semana 2
│
├── Validación bootstrap
├── Prueba de permutación
├── Bootstrap de correlaciones
├── Simulación Monte Carlo
├── Análisis de robustez
└── Resultados validados para Semana 3
```

---

## Resultados principales validados en Semana 2

La Semana 2 confirma que `Humidity3pm` mantiene una diferencia relevante entre los días asociados a lluvia al día siguiente y los días sin lluvia posterior.

El hallazgo principal de Semana 1, basado en la diferencia de medias de `Humidity3pm` entre `RainTomorrow = Yes` y `RainTomorrow = No`, es validado mediante:

* Bootstrap no paramétrico.
* Intervalos bootstrap percentil.
* Intervalos bootstrap BCa.
* Prueba de permutación.
* Análisis de robustez frente a valores extremos.
* Sensibilidad por localidad.

Además, la Semana 2 identifica variables con estabilidad estadística para ser consideradas en etapas posteriores, entre ellas:

* `Humidity3pm`
* `RainToday_bin`
* `Rainfall`
* `Pressure3pm`
* `MaxTemp`

Estos resultados sirven como insumo metodológico para la preparación de la Sumativa 3.

---

## Requisitos previos

Antes de ejecutar el proyecto, se recomienda contar con:

* Python 3.12.x
* Git
* Visual Studio Code, JupyterLab o Jupyter Notebook
* Sistema operativo Windows, Linux o macOS
* Acceso local al repositorio clonado desde GitHub

---

## Instalación del proyecto

### 1. Clonar el repositorio

```bash
git clone https://github.com/edocontreras/mcdia500-estadistica-computacional-g6.git
```

Ingresar a la carpeta del repositorio:

```bash
cd mcdia500-estadistica-computacional-g6
```

---

### 2. Ingresar a la carpeta semanal

Para ejecutar Semana 1:

```bash
cd semana1
```

Para ejecutar Semana 2:

```bash
cd semana2
```

Para ejecutar Semana 3:

```bash
cd semana3
```

Cada semana posee su propio archivo `requirements.txt`, por lo que se recomienda crear y activar el entorno virtual desde la carpeta semanal que se desea ejecutar.

---

### 3. Crear el entorno virtual

Desde la carpeta semanal correspondiente:

```bash
python -m venv .venv
```

---

### 4. Activar el entorno virtual

En Windows PowerShell:

```bash
.venv\Scripts\Activate.ps1
```

En Linux o macOS:

```bash
source .venv/bin/activate
```

Si la activación fue correcta, en Windows debería observarse una estructura similar a:

```text
(.venv) PS C:\ruta\del\proyecto\semana1>
```

o, según la semana ejecutada:

```text
(.venv) PS C:\ruta\del\proyecto\semana2>
```

---

### 5. Actualizar pip

```bash
python -m pip install --upgrade pip
```

---

### 6. Instalar dependencias

```bash
python -m pip install -r requirements.txt
```

---

### 7. Registrar el entorno virtual como kernel de Jupyter

```bash
python -m ipykernel install --user --name mcdi501-g6 --display-name "Python 3.12 - MCDI501 G6 Est Comp"
```

---

### 8. Ejecutar JupyterLab

```bash
python -m jupyterlab --ServerApp.use_redirect_file=False
```

Dentro de JupyterLab, seleccionar el kernel:

```text
Kernel → Change Kernel → Python 3.12 - MCDI501 G6 Est Comp
```

---

## Ejecución de notebooks

Los notebooks principales se encuentran en:

```text
semana1/notebooks/Sumativa1_Rain_Australia_G6.ipynb
semana2/notebooks/Sumativa2_Rain_Australia_G6.ipynb
```

Se recomienda ejecutar los notebooks en orden cronológico:

```text
1. Semana 1
2. Semana 2
3. Semana 3
```

Esto permite mantener la trazabilidad entre los productos generados en cada etapa.

---

## Importación de módulos auxiliares

Desde un notebook ubicado en la carpeta `notebooks/`, se pueden importar funciones desde la carpeta `src/` utilizando:

```python
import sys
from pathlib import Path

project_root = Path.cwd().parent
sys.path.append(str(project_root / "src"))
```

Ejemplo de carga de datos en Semana 1:

```python
import pandas as pd

df = pd.read_csv("../data/raw/weatherAUS.csv")
df.head()
```

Ejemplo de carga de datos en Semana 2:

```python
import pandas as pd

df = pd.read_csv("../data/input/weatherAUS_sumativa1_variables_clave.csv")
df.head()
```

---

## Reproducibilidad

Para reproducir la Semana 1 desde cero:

```bash
git clone https://github.com/edocontreras/mcdia500-estadistica-computacional-g6.git
cd mcdia500-estadistica-computacional-g6/semana1
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user --name mcdi501-g6 --display-name "Python 3.12 - MCDI501 G6 Est Comp"
python -m jupyterlab --ServerApp.use_redirect_file=False
```

Para reproducir la Semana 2:

```bash
git clone https://github.com/edocontreras/mcdia500-estadistica-computacional-g6.git
cd mcdia500-estadistica-computacional-g6/semana2
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user --name mcdi501-g6 --display-name "Python 3.12 - MCDI501 G6 Est Comp"
python -m jupyterlab --ServerApp.use_redirect_file=False
```

La ejecución completa de la Semana 2 puede requerir mayor tiempo de procesamiento que la Semana 1, debido a que utiliza procedimientos computacionalmente intensivos como bootstrap, intervalos BCa, prueba de permutación y simulación Monte Carlo con un mínimo de 10.000 iteraciones o remuestras, según corresponda.

---

## Archivos principales del proyecto

### Semana 1

```text
semana1/data/raw/weatherAUS.csv
semana1/data/processed/weatherAUS_sumativa1_variables_clave.csv
semana1/notebooks/Sumativa1_Rain_Australia_G6.ipynb
semana1/src/estadistica_utils.py
semana1/docs/inventario_outputs_sumativa1.csv
semana1/docs/informe_sumativa1_rain_australia_g6.docx
semana1/docs/informe_sumativa1_rain_australia_g6.pdf
```

### Semana 2

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

---

## Control de versiones

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
git commit -m "docs: actualiza README principal del proyecto"
```

Para subir los cambios a GitHub:

```bash
git push
```

---

## Archivos que no deben subirse al repositorio

La carpeta `.venv/` no debe subirse a GitHub, ya que cada integrante debe crear su propio entorno virtual local a partir del archivo `requirements.txt`.

El archivo `.gitignore` debe considerar al menos:

```text
.venv/
__pycache__/
.ipynb_checkpoints/
*.pyc
.env
logs/
.vscode/
```

---

## Criterios metodológicos considerados

El proyecto mantiene los siguientes criterios generales:

* Trazabilidad entre datos originales, datos procesados y resultados exportados.
* Separación entre notebooks, módulos auxiliares, tablas y figuras.
* Uso de funciones reutilizables para evitar duplicación innecesaria de código.
* Exportación sistemática de resultados en formato `.csv`.
* Exportación de figuras para uso en informes técnicos.
* Documentación de salidas mediante inventarios.
* Continuidad metodológica entre Semana 1, Semana 2 y Semana 3.
* Preparación de insumos validados para etapas posteriores del proyecto.

---

## Integrantes

* Eduardo Contreras
* Gonzalo Bouldres
* Luis Díaz Giral

---

## Docente

Dr. Jean Paul Maidana González

---

## Curso

**MCDI501 - Estadística Computacional para la Toma de Decisiones**
