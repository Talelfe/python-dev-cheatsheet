# guia-entornos-VSC
📓 Guía personal para la creación y gestión de entornos virtuales de Python directamente desde la interfaz de Visual Studio Code. 💻

## 💻 **Creación y Gestión de Entornos en VS Code**
Crear y gestionar entornos virtuales en VS Code es más fácil de lo que parece, ya que el editor automatiza muchos de los pasos. Puedes hacerlo directamente desde la interfaz gráfica o con la terminal integrada.

1. **Crear un entorno virtual**
La forma más sencilla es usar la **paleta de comandos** de VS Code.

1. Abre la paleta de comandos con `Ctrl` + `Shift` + `P`.

2. Escribe `Python: Create Environment` y presiona `Enter`.

3. Selecciona el tipo de entorno que quieres crear (`Venv` o `Conda`).

4. VS Code te pedirá que elijas una versión de Python para usar en el entorno. Selecciona la que necesites.

Después de unos segundos, VS Code creará la carpeta del entorno virtual dentro de tu proyecto y la activará automáticamente.

2. **Cambiar de entorno (Seleccionar intérprete)**

Para cambiar de entorno en un proyecto abierto, usa el Selector de intérpretes.

1. Abre la paleta de comandos con `Ctrl` + `Shift` + `P`.

2. Escribe `Python: Select Interpreter` y presiona `Enter`.

3. VS Code te mostrará una lista de todos los entornos virtuales detectados, incluyendo los que creaste.

Selecciona el entorno que deseas usar (por ejemplo, `Python`: `Venv`).

## 🔍 **Revisar y Eliminar Entornos Virtuales**

Para revisar los entornos que tienes creados por tu cuenta, puedes usar la terminal.

1. Abre la terminal integrada de VS Code (`Ctrl` + `ñ`).

2. Ejecuta este comando: `conda env list` o `conda info --envs`.

3. Este comando te mostrará una lista de todos los entornos de `Conda` que has creado, incluyendo su ubicación en el disco.

### Eliminar un entorno virtual

No hay un comando directo para eliminar un entorno desde VS Code. La forma más segura y simple es **borrar la carpeta del entorno virtual** directamente.

1. Abre el Explorador de Archivos de VS Code (a la izquierda).

2. Busca la carpeta de tu entorno (generalmente se llama `mi_entorno` o `venv`).

3. Haz clic derecho sobre la carpeta y selecciona **"Delete"**.

## ❓ Preguntas Adicionales

**¿Es lo mismo que crear librerías por medio de líneas de código?**
No, no es lo mismo. Un entorno virtual es un **contenedor** para tus librerías. Creas el entorno (`python3 -m venv mi_entorno`) y luego instalas las librerías **dentro de ese contenedor** (`pip install pandas`). La línea de código para crear el entorno es un paso de configuración, mientras que la instalación de librerías es un paso de contenido.

**`Venv` vs. `Conda`**
* `Venv`: Es la herramienta nativa de Python. Es más ligera, simple y solo gestiona paquetes de Python. Es la opción preferida si tu proyecto solo necesita librerías de Python.

* `Conda`: Es un gestor de paquetes de código abierto que puede gestionar entornos para cualquier lenguaje de programación (Python, R, etc.). `Conda` es más potente y puede gestionar tanto librerías de Python como paquetes que no son de Python (como librerías de C++ o de `R`), lo cual es útil en ciencia de datos.

**¿Qué significan las opciones que te aparecen?**
Cuando seleccionas `Python: Select Interpreter`, VS Code te muestra los intérpretes de Python que ha detectado en tu sistema.

* `Python D:\Anaconda\envs\mi_entorno\python.exe`

  * Esto es un **entorno virtual de Conda.**
 
  * `D:\Anaconda\envs\mi_entorno`: Es la ubicación de la carpeta de este entorno.

  * `python.exe`: Es el ejecutable de Python dentro de ese entorno.

  * Para ver las librerías, activa ese entorno en la terminal de VSC y usa `pip list`.

* `Python 3.13.5 (base) D:\Anaconda\python.exe`

  * Esto es tu **entorno base de Conda.**

  * `D:\Anaconda\python.exe`: Es el intérprete de Python principal de tu instalación de Anaconda.

  * El término `(base)` se refiere al entorno por defecto de Conda. Cuando abres la terminal de Anaconda, estás en el entorno `base` a menos que actives otro.

  * Para ver las librerías, activa el entorno `base` y usa `pip list`.

Ambas opciones son entornos válidos, pero recuerda que el objetivo es crear y usar entornos virtuales para cada uno de tus proyectos. La opción `base` es para cuando no estás trabajando en un proyecto específico o si necesitas usar las herramientas globales de Anaconda.
