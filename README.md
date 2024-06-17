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
    git clone https://github.com/tu-usuario/library-management-system.git
    cd library-management-system
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
