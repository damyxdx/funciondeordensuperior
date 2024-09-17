Funciones de Orden Superior con Interfaz Gráfica
Este proyecto es una aplicación en Python que permite cargar y analizar datos de estudiantes utilizando funciones de orden superior. Los datos de los estudiantes (nombre, fecha de nacimiento y calificaciones) pueden ser cargados desde un archivo PDF, y la aplicación cuenta con una interfaz gráfica simple para visualizar la información procesada.

Características
Cargar datos desde un PDF: Permite cargar los nombres, fechas de nacimiento y calificaciones de los estudiantes desde un archivo PDF.
Funciones de Orden Superior: Utiliza funciones de orden superior para realizar análisis de los datos, tales como:
Promedio de calificaciones por estudiante.
Mejores estudiantes (con un promedio mayor o igual a 9).
Ordenar a los estudiantes por fecha de nacimiento (de más joven a más viejo).
Obtener la mayor calificación registrada entre todos los estudiantes.
Interfaz gráfica: Interfaz gráfica sencilla hecha con tkinter que facilita el uso de las funcionalidades del programa.
Requisitos
Python 3.x
Librerías necesarias:
tkinter (viene por defecto con Python)
PyPDF2
Para instalar las librerías necesarias, puedes ejecutar:

bash

pip install PyPDF2
Instrucciones de uso
Clonar o descargar el repositorio:

bash

git clone <URL del repositorio>
cd <nombre del directorio>
Cargar los datos desde un PDF:

Asegúrate de tener un archivo PDF que contenga los datos de los estudiantes en el siguiente formato:
bash

Nombre, Fecha de Nacimiento (dd/mm/yyyy), Calificaciones (separadas por comas)
Ejemplo:
Copiar código
Carlos, 15/04/2002, 7.5, 8, 9
Ana, 22/08/2001, 9.5, 9.2, 8.8
Al iniciar la aplicación, utiliza el botón "Cargar Datos desde PDF" para seleccionar el archivo PDF.
Análisis de datos:

Después de cargar los datos, puedes usar los siguientes botones para ver los resultados:
Mostrar Promedios: Muestra el promedio de calificaciones por cada estudiante.
Mejores Estudiantes: Muestra una lista de estudiantes con un promedio mayor o igual a 9.
Ordenar por Nacimiento: Muestra la lista de estudiantes ordenada por fecha de nacimiento (de más joven a más viejo).
Mayor Calificación: Muestra la mayor calificación registrada entre todos los estudiantes.
Estructura del Proyecto
main.py: Archivo principal donde se encuentra el código del programa, incluyendo la interfaz gráfica y la lógica de las funciones de orden superior.
requirements.txt: Lista de dependencias necesarias para ejecutar el programa.
Ejemplo de uso
Ejecuta el archivo main.py:

bash
python main.py
En la interfaz gráfica:

Carga un archivo PDF con el botón "Cargar Datos desde PDF".
Usa los botones para realizar el análisis deseado:
Mostrar los promedios de los estudiantes.
Ver los mejores estudiantes.
Ordenar a los estudiantes por fecha de nacimiento.
Obtener la mayor calificación registrada.
Formato del PDF
El archivo PDF debe tener un formato como el siguiente:

css

Carlos, 15/04/2002, 7.5, 8, 9
Ana, 22/08/2001, 9.5, 9.2, 8.8
Lucía, 11/01/2000, 6.7, 7.1, 6.9
Pedro, 30/12/2003, 10, 9.8, 9.9
María, 19/05/2002, 9, 8.8, 9.5
Tecnologías Utilizadas
Python 3.x
tkinter: Para la creación de la interfaz gráfica.
PyPDF2: Para la extracción de texto desde archivos PDF.

Contribuciones
Si deseas contribuir a este proyecto, por favor sigue los pasos:

Haz un fork del repositorio.

Crea una nueva rama:

git checkout -b feature/nueva-funcionalidad

Realiza tus cambios y haz un commit:

git commit -m "Añadida nueva funcionalidad"

Sube tus cambios a tu rama:

git push origin feature/nueva-funcionalidad
Crea un Pull Request en este repositorio.
