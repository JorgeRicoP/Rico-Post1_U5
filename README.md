# Biblioteca API - CRUD con Spring Boot, JPA y Repository

## Descripción del Proyecto

Este proyecto consiste en el desarrollo de una API REST para la gestión de libros, implementada con Spring Boot. La aplicación permite realizar operaciones CRUD (Crear, Leer, Actualizar y Eliminar) sobre una entidad `Libro`, utilizando una base de datos en memoria H2.

El objetivo principal es aplicar el patrón de diseño **Repository** junto con una arquitectura en capas, separando claramente las responsabilidades entre las distintas partes del sistema.

---

## Arquitectura del Proyecto

El proyecto sigue una arquitectura en capas basada en el patrón MVC y el uso del patrón Repository. Las capas implementadas son:

* **Model (Entity):**
  Contiene la clase `Libro`, la cual representa la estructura de la tabla en la base de datos mediante anotaciones JPA.

* **Repository:**
  Define la interfaz `LibroRepository`, que extiende `JpaRepository`. Esta capa se encarga del acceso a datos y permite realizar operaciones CRUD sin necesidad de escribir consultas SQL manualmente.

* **Service:**
  Implementa la lógica de negocio en la clase `LibroService`. Aquí se manejan validaciones y reglas como la verificación de ISBN duplicados.

* **Controller:**
  La clase `LibroController` expone los endpoints REST y gestiona las solicitudes HTTP, delegando la lógica al servicio correspondiente.

Esta separación permite una mejor mantenibilidad, escalabilidad y organización del código.

---

## Tecnologías y Dependencias

El proyecto utiliza las siguientes tecnologías:

* Java 17
* Spring Boot
* Spring Web
* Spring Data JPA
* H2 Database (base de datos en memoria)
* Lombok
* Validation (Jakarta Validation)
* Maven

---

## Cómo Ejecutar el Proyecto

1. Clonar el repositorio:

```
git clone https://github.com/JorgeRicoP/Rico-Post1_U5/
```

2. Abrir el proyecto en IntelliJ IDEA o VS Code.

3. Ejecutar la clase principal:

```
BibliotecaApiApplication.java
```

O desde terminal:

```
mvn spring-boot:run
```

4. Acceder a la aplicación:

* API REST:
  http://localhost:8080

* Consola H2:
  http://localhost:8080/h2-console

Configuración para H2:

* JDBC URL: `jdbc:h2:mem:biblioteca_db`
* Usuario: `sa`
* Contraseña: (vacío)

---

## Endpoints Disponibles

### 1. Listar todos los libros

**GET**

```
/api/libros
```

---

### 2. Obtener libro por ID

**GET**

```
/api/libros/{id}
```

---

### 3. Crear un libro

**POST**

```
/api/libros
```

**Body (JSON):**

```
{
  "titulo": "Clean Code",
  "autor": "Robert C. Martin",
  "isbn": "123456",
  "anioPublicacion": 2008,
  "categoria": "Software"
}
```

---

### 4. Actualizar un libro

**PUT**

```
/api/libros/{id}
```

---

### 5. Eliminar un libro

**DELETE**

```
/api/libros/{id}
```

---

### 6. Buscar libros por palabra clave

**GET**

```
/api/libros/buscar?q=texto
```

---

## Evidencias de Funcionamiento

A continuación se presentan evidencias del funcionamiento de la API:

* Creación de libro (POST)
* Listado de libros (GET)
* Eliminación de libro (DELETE)
* Consulta en la base de datos H2

Estas se encuentran en la carpeta /captures

---

## Pruebas

El proyecto incluye la clase:

```
BibliotecaApiApplicationTests.java
```

La cual permite verificar que el contexto de Spring Boot se carga correctamente.

---

## Control de Versiones

El desarrollo del proyecto se realizó mediante commits descriptivos que reflejan el progreso incremental:

1. Inicialización del proyecto y configuración base
2. Implementación de la entidad y capa Repository
3. Implementación de Service y Controller
4. Documentación, pruebas y evidencias
