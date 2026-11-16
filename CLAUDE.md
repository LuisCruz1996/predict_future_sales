# CLAUDE.md

Reglas que se siguen siempre en este proyecto.

## Contexto

- Proyecto: EDA del dataset Predict Future Sales (Kaggle) para un curso de maestría. El enunciado está dividido en secciones 1 a 10.
- Notebook principal: `notebooks/01_exploratory_data_analysis.ipynb`. Ese nombre lo exige el curso; no usar otra convención.
- Entorno y kernel: `env_future_sales` (`C:\Users\luisi\anaconda3\envs\env_future_sales`). Conda no está en el PATH:
  - Python: `C:\Users\luisi\anaconda3\envs\env_future_sales\python.exe`
  - Conda: `C:\Users\luisi\anaconda3\Scripts\conda.exe`

## Notebook

- Antes de cada celda de código va una celda markdown con un título numerado según la sección del enunciado (por ejemplo `## 4. Análisis de valores faltantes` y `### 4.a ...`) y una descripción breve, directa y profesional, en español.
- En el código, comentarios solo donde aporten.
- Después de cada gráfica o tabla relevante va una celda markdown **Interpretación** con lo que muestran los datos, usando las cifras reales obtenidas al ejecutar el notebook.
- Gráficas: `sns.set_theme(style="whitegrid")`, título, ejes con etiqueta, separador de miles en los valores grandes y `tight_layout`.
- Carga de datos con rutas parametrizadas y una función que lance `FileNotFoundError("No se encontró el archivo: ...")`.
- Después de editar el notebook, ejecutarlo completo para validarlo y guardar las salidas (bash):

  ```
  PYTHONNOUSERSITE=1 /c/Users/luisi/anaconda3/envs/env_future_sales/python.exe -m nbconvert --to notebook --execute --inplace notebooks/01_exploratory_data_analysis.ipynb
  ```

  - Usar `-m nbconvert`, no `-m jupyter nbconvert`: este último resuelve a otro Jupyter del PATH del sistema.
  - `PYTHONNOUSERSITE=1` evita que se carguen paquetes de `AppData\Roaming\Python\Python311\site-packages`, que
    tapan a los del entorno (ipykernel, IPython, zmq...). El kernelspec `env_future_sales` ya lo define en su `env`.

  Luego resumir los resultados clave.

## Datos y dependencias

- `data/raw` nunca se modifica ni se sube al repositorio.
- Si se agrega una librería, instalarla en `env_future_sales` y añadirla a `requirements.txt` y `environment.yml` en su categoría.
- Instalar desde conda-forge y mantener OpenBLAS (`libblas=*=*openblas`); no usar MKL, porque hacía caer el kernel de VS Code.

## General

- Hacer solo lo que pide cada prompt.
