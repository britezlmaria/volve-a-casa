#  Volvé a Casa - Plataforma de Recuperación de Mascotas

**Volvé a Casa** es una aplicación integral diseñada para facilitar el reencuentro de mascotas perdidas con sus familias. La plataforma permite a los usuarios reportar desapariciones, registrar avistamientos geolocalizados y gestionar perfiles de búsqueda mediante una arquitectura robusta y moderna.

##  Equipo de Desarrollo 
* [Vicente Garcia Marti](https://github.com/Vicen621)
* [Matias Guaymas](https://github.com/MatiasGuaymas/MatiasGuaymas)
* [Matheo Lamiral](https://github.com/MatheoLamiral/MatheoLamiral)
* [Maria Luisa Britez](https://github.com/britezlmaria/britezlmaria)

##  Stack Tecnológico

### Backend (Spring Boot)
* **Java & Spring Boot:** Núcleo de la aplicación y exposición de API RESTful.
* **Spring Security:** Gestión de autenticación y autorización basada en roles como `ADMIN` y `USER`.
* **Spring Data JPA:** Manejo de persistencia con soporte para paginación, ordenamiento y filtros complejos.
* **Jakarta Validation:** Validación de integridad de datos en DTOs para garantizar información consistente.

### Frontend (Angular)
* **Angular:** Framework principal para una experiencia de usuario fluida y reactiva.
* **Tailwind CSS:** Estilizado moderno y responsivo con soporte para modo oscuro.
* **Leaflet:** Integración de mapas interactivos para geolocalización precisa.
* **Reactive Forms:** Gestión avanzada de formularios con validaciones en tiempo real para el alta y edición de mascotas.

## Funcionalidades Principales

###  Gestión de Mascotas
* **Alta y Edición:** Registro detallado que incluye nombre, raza, tamaño, peso, color y descripción.
* **Mapa de Desaparición:** Los usuarios pueden marcar en un mapa interactivo el punto exacto donde se perdió la mascota.
* **Gestión de Estados:** Seguimiento de la mascota mediante estados como `PERDIDO_PROPIO`, `PERDIDO_AJENO`, `RECUPERADO` y `ADOPTADO`.
* **Carga de Imágenes:** Sistema de carga de fotos convertidas a Base64 para su almacenamiento y visualización.

###  Sistema de Avistamientos
* **Reportes Colaborativos:** Los ciudadanos pueden reportar avistamientos de mascotas en la vía pública.
* **Evidencia Fotográfica:** Cada reporte permite adjuntar una foto del avistamiento y comentarios adicionales.
* **Ubicación en Tiempo Real:** Mapa dedicado para señalar dónde fue vista la mascota por última vez.

###  Perfiles y Administración
* **Roles de Usuario:** Diferenciación entre usuarios estándar y administradores con permisos extendidos.
* **Moderación Admin:** Los administradores pueden gestionar el estado de los usuarios y editar información crítica.
* **Privacidad:** Acceso a perfiles públicos para facilitar el contacto entre dueños y rescatistas.

---

##  Configuración del Entorno

###  Backend (Spring Boot)
El servidor está construido con **Spring Boot 3** y utiliza **Maven** para la gestión de dependencias.

#### Requisitos:
* **JDK 17** o superior.
* **Maven 3.8+**
* Base de datos configurada en el archivo `application.properties`.

#### Pasos para ejecutar:
1. Dirigite al directorio raíz del backend.
2. Configura tus credenciales de base de datos en `src/main/resources/application.properties`.
3. Ejecuta los comandos:
   ```bash
   mvn clean install
   mvn spring-boot:run
