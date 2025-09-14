# guia-entornos-ubuntu
📓 Guía paso a paso sobre la creación, activación y gestión de entornos virtuales de Python en la terminal de Ubuntu. 🐧

# 🐍 Guía Rápida de Entornos Virtuales en Ubuntu

Los entornos virtuales son tu mejor amigo en Python. Te permiten aislar las dependencias de cada proyecto, evitando conflictos entre versiones. ¡Adiós a los dolores de cabeza! 🤯

⚙️ **Preparación del Entorno (Nivel Global)**

Antes de comenzar, es una buena práctica asegurarte de que los paquetes del sistema estén actualizados.

`sudo apt update`

Este comando actualiza la lista de software disponible en los repositorios de Ubuntu.
Esas librerías no se instalan solas. Debes instalarlas explícitamente usando el comando pip install para cada una de ellas.
Puedes instalarlas a nivel de sistema o dentro de una carpeta virtual, pero la mejor práctica es siempre instalarlas en un entorno virtual.

## 🚀 Creando y Activando tu Entorno

1️⃣ **Crear el entorno**

Te recomiendo crear el entorno virtual dentro de la carpeta de tu proyecto. 

`python3 -m venv nombre_del_entorno`

  * `python3 -m venv`: Le dice a Python que use el módulo venv para crear un nuevo entorno.
  * `nombre_del_entorno`: Es el nombre de la carpeta que se creará para tu entorno.

2️⃣ Activar y desactivar

Al activar el entorno, tu terminal sabrá que debe usar los paquetes de este entorno, no los globales.

* **Activar:**
  `source nombre_del_entorno/bin/activate`

  * `source`: Es un comando de la terminal que ejecuta un script.
  * `nombre_del_entorno/bin/activate`: Es el script que activa el entorno.

* **Desactivar:**

  `deactivate`
  
  * Este comando te saca del entorno virtual, volviendo a la configuración global de tu sistema.

## 📦 Instalando Librerías

1️⃣ Con `pip`

`pip` es el gestor de paquetes de Python. Es la forma más común de instalar librerías.

`pip install nombre_de_la_libreria`

  * `pip`: El gestor de paquetes de Python.

  * `install`: La acción de instalar.

  * `nombre_de_la_libreria`: El paquete que quieres. ¡Y listo!

🚨 ¡Importante! Nunca uses `sudo` dentro de un entorno virtual. Si lo haces, `pip` ignorará el entorno e intentará instalar el paquete a nivel del sistema, lo cual puede generar conflictos (`externally-managed-environment`).

2️⃣ Con requirements.txt

Esta es la mejor forma de gestionar las librerías de tu proyecto. El archivo `requirements.txt` es una lista de todas las librerías necesarias.

* **Crear el archivo:**

`pip freeze > requirements.txt`

Este comando congela tu entorno actual y crea el archivo `requirements.txt` con los nombres y las versiones exactas de cada librería.

* **Instalar desde el archivo:**

`pip install -r requirements.txt`

El parámetro `-r` le indica a `pip` que lea la lista de librerías del archivo y las instale todas de una vez.

## 🧩 Paquetes del Sistema vs. Paquetes del Entorno

Es crucial entender la diferencia para evitar errores.

* **Paquetes del sistema (globales):** Son gestionados por el sistema operativo con `apt`. Son librerías de bajo nivel necesarias para que programas del sistema funcionen.

  * **Comando:** `sudo apt install nombre_paquete`

  * **Ejemplos:** `python3-psycopg2`, `python3.12-venv`, `postgresql`.

✨ Nota: sudo (del inglés "super user do") te permite ejecutar un comando como si fueras el usuario root. Al usarlo, se te pedirá una contraseña de usuario para confirmar que tienes permiso.

* **Paquetes del entorno virtual:** Son gestionados por `pip`. Son las librerías que tu proyecto necesita (pandas, SQLAlchemy, etc.).

  * **Comando:** `pip install nombre_de_la_libreria`

## 💡 Resolviendo tus Dudas

**1. ¿Cómo revisar si hay conflictos de librerías globales?**

La forma más directa es usar `pip check`. Este comando analiza las dependencias instaladas y te notifica si hay algún conflicto.

`pip check`

Si todo está bien, no te mostrará nada. Si detecta problemas, te dirá qué paquetes tienen dependencias rotas.
Puedes ejecutar el comando `pip check` tanto a nivel global como dentro de tu entorno virtual. La diferencia radica en dónde busca conflictos de dependencias.

  * `pip check` **a Nivel Global**

    * Cuando lo ejecutas sin activar un entorno virtual, `pip` revisa la instalación de Python de tu **sistema operativo**. Esto te muestra si alguna de las librerías del sistema (como las que Ubuntu usa internamente) tiene un problema de dependencias. Si todo va bien muestra `No broken requirements found`.

    * **¿Cuándo usarlo?** Para un diagnóstico general de tu instalación de Python a nivel de sistema.

  * `pip check` **dentro del Entorno Virtual**

    * Cuando lo ejecutas después de activar un entorno virtual (nombre_del_entorno), pip revisa exclusivamente las librerías que has instalado para tu **proyecto actual**. Esto te ayuda a identificar rápidamente si una librería que acabas de instalar causa un conflicto con otra que ya estaba en tu proyecto.

    * **¿Cuándo usarlo?** Es la forma más útil de `pip check`. Te permite verificar la salud de las dependencias de tu proyecto de forma aislada, sin que te afecte lo que ocurre a nivel global.


**2. ¿Cómo revisar las versiones de las librerías en mi Ubuntu?**

Puedes usar el mismo `pip` a nivel global (fuera de cualquier entorno virtual) para ver lo que está instalado en tu sistema.

`pip3 list`

Este comando te mostrará todas las librerías instaladas globalmente. Para evitar un conflicto con el externally-managed-environment, a veces es necesario usar pip3 list de forma directa para evitar el error.



### 📦 Librerías de Python para `pip`

| Categoría	                      | Librerías Populares                               | Descripción |
| ------------------------------- | ------------------------------------------------- | ------------ |
| **Ciencia de Datos** 📊        | `pandas`, `NumPy`, `Scikit-learn`                  | Manipulación de datos, análisis, álgebra lineal y aprendizaje automático. |
| **Visualización** 📈           | `Matplotlib`, `Seaborn`, `Plotly`                  | Creación de gráficos estáticos y dinámicos para visualizar datos. |
| **Inteligencia Artificial** 🧠 | `TensorFlow`, `PyTorch`, `Keras`                   |	Frameworks para machine learning y redes neuronales. |
| **Desarrollo Web** 🌐          | `Flask`, `Django`, `FastAPI`                       | Creación de servidores, APIs y aplicaciones web. |
| **Bases de Datos** 🗃️          | `SQLAlchemy`, `psycopg2`, `mysql-connector-python` |	Conexión e interacción con bases de datos relacionales. |
| **Web Scraping** 🕸️            | `requests`, `Beautiful Soup`                       |	Extracción de información de páginas web. |
| **Utilidades** 🛠️              | `rich`, `tqdm`                                     |	Herramientas para mejorar la interfaz de línea de comandos y la experiencia de desarrollo. |
  
