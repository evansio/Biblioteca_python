# Biblioteca_python

## Descripción

Este proyecto es un sistema de gestión de biblioteca desarrollado en Python. Permite a los usuarios realizar varias acciones como agregar libros, prestar libros, devolver libros y registrar usuarios, todo ello interactuando a través de la terminal.

## Características

- **Agregar Libro**: Añade un nuevo libro a la biblioteca o incrementa la cantidad de un libro existente.
- **Mostrar Libros**: Muestra una lista de libros disponibles en la biblioteca junto con su autor, cantidad y disponibilidad.
- **Prestar Libro**: Permite prestar un libro a un usuario registrado.
- **Registrar Usuario**: Registra un nuevo usuario en la biblioteca.
- **Listar Usuarios**: Muestra una lista de todos los usuarios registrados.
- **Listar Libros de Usuario**: Muestra los libros prestados a un usuario específico.
- **Devolver Libro**: Permite a un usuario devolver un libro prestado.
- **Editar Usuario**: Permite editar la información de un usuario registrado.

## Requisitos

- Python 3.x

## Instalación

1. Clona el repositorio:
    ```bash
    git clone https://github.com/evansio/Biblioteca_python.git
    cd library-Biblioteca_python
    ```

2. Instala las dependencias (si es necesario, en este caso, no hay dependencias externas).

## Uso

Para ejecutar la aplicación, simplemente ejecuta el archivo `biblioteca.py`:

```bash
python biblioteca.py
```
## Ejemplos de Uso
### Agregar Libro:

Selecciona la opción 1 en el menú.
Ingresa el título y autor del libro.
### Mostrar Libros:

Selecciona la opción 2 en el menú.
### Prestar Libro:

Selecciona la opción 3 en el menú.
Ingresa el título del libro y el nombre del usuario.
### Registrar Usuario:

Selecciona la opción 4 en el menú.
Ingresa el nombre del usuario.
### Listar Usuarios:

Selecciona la opción 5 en el menú.
### Listar Libros de Usuario:

Selecciona la opción 6 en el menú.
### Ingresa el nombre del usuario.
Devolver Libro:

Selecciona la opción 7 en el menú.
Ingresa el título del libro y el nombre del usuario.
### Editar Usuario:

Selecciona la opción 8 en el menú.
Ingresa el nombre del usuario y luego el nuevo nombre.
### Salir:

Selecciona la opción 9 para guardar los datos y salir del programa.
## Casos de Prueba
### Agregar y Mostrar Libros:

Agrega varios libros y muestra la lista de libros para verificar que se han agregado correctamente.
### Registrar y Listar Usuarios:

Registra varios usuarios y lista los usuarios para verificar que se han registrado correctamente.
Prestar y Listar Libros de Usuario:

Presta un libro a un usuario y verifica que el libro aparezca en la lista de libros prestados del usuario.
### Devolver Libro:

Devuelve un libro prestado y verifica que el libro ya no esté en la lista de libros prestados del usuario y que su cantidad haya aumentado en la biblioteca.
### Editar Usuario:

Edita la información de un usuario y verifica que el cambio se refleje correctamente.
## Contribuciones
### Las contribuciones son bienvenidas. Para contribuir, por favor sigue los siguientes pasos:

- Haz un fork del proyecto.
- Crea una nueva rama (git checkout -b feature/nueva-funcionalidad).
- Realiza tus cambios y haz commit (git commit -am 'Agrega nueva funcionalidad').
- Haz push a la rama (git push origin feature/nueva-funcionalidad).
- Crea un nuevo Pull Request.

  
### Documentación del Código

Añade comentarios al código para documentar las funciones y clases, tal como se muestra a continuación:

```python
import pickle

class Libro:
    """
    Clase para representar un libro en la biblioteca.

    Atributos:
    - titulo: El título del libro.
    - autor: El autor del libro.
    - cantidad: La cantidad de copias disponibles en la biblioteca.
    - disponible: Indica si el libro está disponible para préstamo.
    """
    def __init__(self, titulo, autor, cantidad=1):
        self.titulo = titulo
        self.autor = autor
        self.cantidad = cantidad
        self.disponible = True

class Usuario:
    """
    Clase para representar un usuario de la biblioteca.

    Atributos:
    - nombre: El nombre del usuario.
    - libros_prestados: Lista de libros prestados al usuario.
    """
    def __init__(self, nombre):
        self.nombre = nombre
        self.libros_prestados = []

def agregar_libro(biblioteca, titulo, autor):
    """
    Agrega un libro a la biblioteca o incrementa su cantidad si ya existe.

    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    - titulo: El título del libro a agregar.
    - autor: El autor del libro a agregar.
    """
    for libro in biblioteca['libros']:
        if libro.titulo == titulo:
            libro.cantidad += 1
            break
    else:
        biblioteca['libros'].append(Libro(titulo, autor))
    print("Libro agregado exitosamente.")

def mostrar_libros(biblioteca):
    """
    Muestra la lista de libros en la biblioteca.
    
    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    """
    print("Lista de libros en la biblioteca:")
    for libro in biblioteca['libros']:
        disponibilidad = "Disponible" if libro.disponible else "No disponible"
        print(f"Título: {libro.titulo}, Autor: {libro.autor}, Cantidad: {libro.cantidad}, Disponibilidad: {disponibilidad}")

def prestar_libro(biblioteca, titulo_libro, nombre_usuario):
    """
    Permite prestar un libro a un usuario dado su título y nombre de usuario.
    
    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    - titulo_libro: El título del libro a prestar.
    - nombre_usuario: El nombre del usuario que quiere tomar prestado el libro.
    """
    for libro in biblioteca['libros']:
        if libro.titulo == titulo_libro:
            if libro.disponible and libro.cantidad > 0:
                for usuario in biblioteca['usuarios']:
                    if usuario.nombre == nombre_usuario:
                        usuario.libros_prestados.append(libro)
                        libro.cantidad -= 1
                        libro.disponible = libro.cantidad > 0
                        print("Libro prestado exitosamente.")
                        return
                else:
                    print("Usuario no registrado.")
                    return
            else:
                print("El libro no está disponible en este momento.")
                return
    else:
        print("Libro no encontrado.")

def registrar_usuario(biblioteca, nombre):
    """
    Registra un usuario en la biblioteca.

    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    - nombre: El nombre del usuario a registrar.
    """
    for usuario in biblioteca['usuarios']:
        if usuario.nombre == nombre:
            print("El usuario ya está registrado.")
            return
    biblioteca['usuarios'].append(Usuario(nombre))
    print("Usuario registrado exitosamente.")

def guardar_datos(biblioteca):
    """
    Guarda los datos de la biblioteca en un archivo.

    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    """
    with open('datos_biblioteca.pkl', 'wb') as f:
        pickle.dump(biblioteca, f)
    print("Datos guardados correctamente.")

def cargar_datos():
    """
    Carga los datos previos de la biblioteca desde un archivo.

    Devuelve:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    """
    try:
        with open('datos_biblioteca.pkl', 'rb') as f:
            return pickle.load(f)
    except FileNotFoundError:
        return {'libros': [], 'usuarios': []}

def listar_usuarios(biblioteca):
    """
    Muestra una lista de los usuarios registrados en la biblioteca.

    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    """
    print("Lista de usuarios registrados:")
    for usuario in biblioteca['usuarios']:
        print(usuario.nombre)

def listar_libros_usuario(biblioteca, nombre_usuario):
    """
    Muestra una lista de libros prestados a un usuario específico.

    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    - nombre_usuario: El nombre del usuario cuyos libros prestados se quieren listar.
    """
    for usuario in biblioteca['usuarios']:
        if usuario.nombre == nombre_usuario:
            if usuario.libros_prestados:
                print(f"Libros prestados a {nombre_usuario}:")
                for libro in usuario.libros_prestados:
                    print(f"Título: {libro.titulo}, Autor: {libro.autor}")
            else:
                print(f"{nombre_usuario} no tiene libros prestados.")
            return
    else:
        print("Usuario no encontrado.")

def devolver_libro(biblioteca, titulo_libro, nombre_usuario):
    """
    Permite a un usuario devolver un libro prestado.

    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    - titulo_libro: El título del libro a devolver.
    - nombre_usuario: El nombre del usuario que quiere devolver el libro.
    """
    for usuario in biblioteca['usuarios']:
        if usuario.nombre == nombre_usuario:
            for libro in usuario.libros_prestados:
                if libro.titulo == titulo_libro:
                    usuario.libros_prestados.remove(libro)
                    for libro_biblioteca in biblioteca['libros']:
                        if libro_biblioteca.titulo == titulo_libro:
                            libro_biblioteca.cantidad += 1
                            libro_biblioteca.disponible = True
                            print("Libro devuelto exitosamente.")
                            return
                    else:
                        print("Libro no encontrado en la biblioteca.")
                        return
            else:
                print("Libro no prestado a este usuario.")
                return
    else:
        print("Usuario no encontrado.")

def editar_usuario(biblioteca, nombre_usuario):
    """
    Permite editar el nombre de un usuario registrado.

    Parámetros:
    - biblioteca: Diccionario que contiene la información de la biblioteca.
    - nombre_usuario: El nombre del usuario a editar.
    """
    for usuario in biblioteca['usuarios']:
        if usuario.nombre == nombre_usuario:
            print(f"Editando información de {nombre_usuario}:")
            nuevo_nombre = input("Ingrese el nuevo nombre del usuario: ")
            usuario.nombre = nuevo_nombre
            print("Información del usuario actualizada exitosamente.")
            return
    else:
        print("Usuario no encontrado.")

def mostrar_menu():
    """
    Muestra el menú de opciones disponibles.
    """
    print("\n--- Menú ---")
    print("1. Agregar Libro")
    print("2. Mostrar Libros")
    print("3. Prestar Libro")
    print("4. Registrar Usuario")
    print("5. Listar Usuarios")
    print("6. Listar Libros de Usuario")
    print("7. Devolver Libro")
    print("8. Editar Usuario")
    print("9. Salir")

def main():
    """
    Función principal para ejecutar el sistema de gestión de biblioteca.
    """
    biblioteca = cargar_datos()

    while True:
        mostrar_menu()
        opcion = input("Seleccione una opción: ")

        if opcion == "1":
            titulo = input("Ingrese el título del libro: ")
            autor = input("Ingrese el autor del libro: ")
            agregar_libro(biblioteca, titulo, autor)
        elif opcion == "2":
            mostrar_libros(biblioteca)
        elif opcion == "3":
            titulo_libro = input("Ingrese el título del libro: ")
            nombre_usuario = input("Ingrese el nombre del usuario: ")
            prestar_libro(biblioteca, titulo_libro, nombre_usuario)
        elif opcion == "4":
            nombre_usuario = input("Ingrese el nombre del usuario: ")
            registrar_usuario(biblioteca, nombre_usuario)
        elif opcion == "5":
            listar_usuarios(biblioteca)
        elif opcion == "6":
            nombre_usuario = input("Ingrese el nombre del usuario: ")
            listar_libros_usuario(biblioteca, nombre_usuario)
        elif opcion == "7":
            titulo_libro = input("Ingrese el título del libro: ")
            nombre_usuario = input("Ingrese el nombre del usuario: ")
            devolver_libro(biblioteca, titulo_libro, nombre_usuario)
        elif opcion == "8":
            nombre_usuario = input("Ingrese el nombre del usuario a editar

```
