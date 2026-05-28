# 🎓 Gestión de Estudiantes

Aplicación web CRUD desarrollada con **Spring Boot 3** para la administración de estudiantes universitarios. Permite registrar, consultar, editar y eliminar estudiantes a través de una interfaz web construida con Thymeleaf.

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Versión |
|---|---|
| Java | 23 |
| Spring Boot | 3.5.14 |
| Spring Data JPA | — |
| Spring Validation | — |
| Thymeleaf | — |
| MySQL | — |
| Maven | — |

---

## 📁 Estructura del proyecto

```
src/
└── main/
    ├── java/com/universidad/estudiantes/
    │   ├── EstudiantesApplication.java       # Clase principal
    │   ├── controller/
    │   │   └── EstudianteController.java     # Controlador MVC
    │   ├── model/
    │   │   └── Estudiante.java               # Entidad JPA
    │   ├── repository/
    │   │   └── EstudianteRepository.java     # Repositorio Spring Data
    │   └── service/
    │       └── EstudianteService.java        # Lógica de negocio
    └── resources/
        ├── application.properties            # Configuración
        └── templates/estudiantes/
            ├── lista.html                    # Listado de estudiantes
            ├── formulario.html               # Crear / editar estudiante
            └── confirmar-eliminar.html       # Confirmación de eliminación
```

---

## 🗃️ Modelo de datos

La entidad `Estudiante` contiene los siguientes campos:

| Campo | Tipo | Restricciones |
|---|---|---|
| `id` | Long | PK, autoincremental |
| `nombre` | String | Obligatorio, 2–100 caracteres |
| `apellido` | String | Obligatorio, máx. 100 caracteres |
| `correo` | String | Obligatorio, único, formato email válido |
| `carrera` | String | Obligatorio, máx. 100 caracteres |

---

## 🌐 Rutas disponibles

| Método | Ruta | Descripción |
|---|---|---|
| GET | `/estudiantes` | Listar todos los estudiantes |
| GET | `/estudiantes/nuevo` | Formulario de registro |
| POST | `/estudiantes/guardar` | Guardar nuevo o editar existente |
| GET | `/estudiantes/editar/{id}` | Formulario de edición |
| GET | `/estudiantes/eliminar/{id}` | Confirmación de eliminación |
| POST | `/estudiantes/eliminar/{id}` | Eliminar estudiante |

---

## ⚙️ Configuración

Edita el archivo `src/main/resources/application.properties` con los datos de tu base de datos MySQL:

```properties
spring.application.name=estudiantes

spring.datasource.url=jdbc:mysql://localhost:3306/estudiantes_db
spring.datasource.username=tu_usuario
spring.datasource.password=tu_contraseña
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

> Asegúrate de crear la base de datos `estudiantes_db` en MySQL antes de ejecutar la aplicación.

---

## 🚀 Cómo ejecutar el proyecto

### Prerequisitos

- Java 23
- Maven 3.x
- MySQL en ejecución

### Pasos

1. Clona el repositorio:
   ```bash
   git clone https://github.com/WilliamBalaguera/balaguera-post1-u8.git
   cd balaguera-post1-u8
   ```

2. Configura las credenciales de base de datos en `application.properties`.

3. Ejecuta la aplicación:
   ```bash
   ./mvnw spring-boot:run
   ```

4. Abre tu navegador en:
   ```
   http://localhost:8080/estudiantes
   ```

---

## 🧪 Pruebas

El proyecto incluye una clase base de pruebas con Spring Boot Test. Para ejecutarlas:

```bash
./mvnw test
```

---

## 📌 Notas adicionales

- El repositorio expone métodos de búsqueda adicionales: por carrera (`findByCarreraIgnoreCase`) y por nombre o apellido (`findByNombreContainingOrApellidoContaining`), listos para ser consumidos desde el servicio.
- Las validaciones del formulario se aplican mediante Bean Validation (`@NotBlank`, `@Email`, `@Size`) y son manejadas automáticamente por Spring MVC.

---

## 👤 Autor

**William Balaguera**
