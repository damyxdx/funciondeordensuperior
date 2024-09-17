import tkinter as tk
from tkinter import messagebox, filedialog
from datetime import datetime
import PyPDF2

# Clase Estudiante
class Estudiante:
    def __init__(self, nombre, fecha_nacimiento, calificaciones):
        self.nombre = nombre
        self.fecha_nacimiento = datetime.strptime(fecha_nacimiento, '%d/%m/%Y')
        self.calificaciones = calificaciones

    def promedio(self):
        return sum(self.calificaciones) / len(self.calificaciones) if self.calificaciones else 0

# Lista de estudiantes (inicialmente vacía, los datos vendrán del PDF)
estudiantes = []

# Funciones de Orden Superior

# 1. Promedio de calificaciones
def obtener_promedios():
    return {est.nombre: est.promedio() for est in estudiantes}

# 2. Mejores estudiantes con promedio >= 9
def mejores_estudiantes():
    return [est.nombre for est in estudiantes if est.promedio() >= 9]

# 3. Ordenar estudiantes por fecha de nacimiento (más joven primero)
def ordenar_por_nacimiento():
    return sorted(estudiantes, key=lambda est: est.fecha_nacimiento, reverse=True)

# 4. Obtener la mayor calificación de todas
def mayor_calificacion():
    return max(max(est.calificaciones) for est in estudiantes)

# Funciones para la interfaz gráfica

def mostrar_promedios():
    promedios = obtener_promedios()
    resultado = "\n".join([f"{nombre}: {promedio:.2f}" for nombre, promedio in promedios.items()])
    messagebox.showinfo("Promedios de Estudiantes", resultado)

def mostrar_mejores_estudiantes():
    mejores = mejores_estudiantes()
    resultado = "\n".join(mejores) if mejores else "Ningún estudiante tiene un promedio mayor o igual a 9."
    messagebox.showinfo("Mejores Estudiantes", resultado)

def mostrar_orden_nacimiento():
    ordenados = ordenar_por_nacimiento()
    resultado = "\n".join([f"{est.nombre}: {est.fecha_nacimiento.strftime('%d/%m/%Y')}" for est in ordenados])
    messagebox.showinfo("Estudiantes por Nacimiento", resultado)

def mostrar_mayor_calificacion():
    mayor = mayor_calificacion()
    messagebox.showinfo("Mayor Calificación", f"La mayor calificación entre todos es: {mayor:.2f}")

# Función para cargar y procesar PDF
def cargar_pdf():
    # Abrir un diálogo para seleccionar el archivo PDF
    file_path = filedialog.askopenfilename(filetypes=[("PDF files", "*.pdf")])
    
    if not file_path:
        return
    
    try:
        with open(file_path, 'rb') as file:
            reader = PyPDF2.PdfReader(file)
            text = ''
            for page in reader.pages:
                text += page.extract_text()

            # Procesar los datos extraídos
            procesar_datos(text)
            messagebox.showinfo("Carga exitosa", "Datos cargados desde el PDF con éxito.")
    
    except Exception as e:
        messagebox.showerror("Error", f"No se pudo procesar el archivo PDF: {str(e)}")

# Función para procesar el texto extraído del PDF y convertirlo en estudiantes
def procesar_datos(texto):
    global estudiantes
    estudiantes = []  # Limpiar la lista actual
    lineas = texto.splitlines()
    
    for linea in lineas:
        try:
            # Asumiendo que el PDF tiene un formato del tipo:
            # Nombre, Fecha de Nacimiento (dd/mm/yyyy), Calificaciones separadas por comas
            # Ejemplo: Carlos, 15/04/2002, 7.5, 8, 9
            datos = linea.split(',')
            nombre = datos[0].strip()
            fecha_nacimiento = datos[1].strip()
            calificaciones = [float(x.strip()) for x in datos[2:]]
            
            # Crear el estudiante y agregarlo a la lista
            estudiante = Estudiante(nombre, fecha_nacimiento, calificaciones)
            estudiantes.append(estudiante)
        
        except Exception as e:
            print(f"Error procesando la línea: {linea}, Error: {e}")

# Crear la interfaz gráfica
ventana = tk.Tk()
ventana.title("Análisis de Estudiantes")
ventana.geometry("400x300")

# Etiqueta de título
label_titulo = tk.Label(ventana, text="Funciones de Orden Superior - Estudiantes", font=("Arial", 14))
label_titulo.pack(pady=10)

# Botón para cargar PDF
btn_cargar_pdf = tk.Button(ventana, text="Cargar Datos desde PDF", command=cargar_pdf)
btn_cargar_pdf.pack(pady=5)

# Botón para mostrar los promedios
btn_promedios = tk.Button(ventana, text="Mostrar Promedios", command=mostrar_promedios)
btn_promedios.pack(pady=5)

# Botón para mostrar los mejores estudiantes
btn_mejores_estudiantes = tk.Button(ventana, text="Mejores Estudiantes", command=mostrar_mejores_estudiantes)
btn_mejores_estudiantes.pack(pady=5)

# Botón para ordenar por fecha de nacimiento
btn_orden_nacimiento = tk.Button(ventana, text="Ordenar por Nacimiento", command=mostrar_orden_nacimiento)
btn_orden_nacimiento.pack(pady=5)

# Botón para mostrar la mayor calificación
btn_mayor_calificacion = tk.Button(ventana, text="Mayor Calificación", command=mostrar_mayor_calificacion)
btn_mayor_calificacion.pack(pady=5)

# Iniciar la ventana
ventana.mainloop()
