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

### Pasos:
   1. Clonar el Repositorio
      ```bash
      git clone https://github.com/Vicen621-Facultad/volve-a-casa.git
      cd volve-a-casa
   2. Crear un archivo .env en la raíz del proyecto con el siguiente contenido:
      # Configuración de PostgreSQL
      POSTGRES_USER=admin
      POSTGRES_PASSWORD=admin
      POSTGRES_DB=grupo01
      
      # Configuración de pgAdmin
      PGADMIN_EMAIL=test@gmail.com
      PGADMIN_PASSWORD=admin
      
      # Configuración de Email (Gmail SMTP)
      MAIL_USERNAME=volveacasattps@gmail.com
      MAIL_PASSWORD=wcvt vuvk gaok dudp
      
      # Bot de Telegram
      TELEGRAM_BOT_TOKEN=tu-telegram-bot-token
      
      # APIs de IA
      GROQ_API_KEY=tu-groq-api-key
      OPENAI_KEY=tu-openai-api-key

##  Configuración del Entorno
   ###  Backend (Spring Boot)
   1. Levantar servicios de infraestructura (PostgreSQL, pgAdmin):
         ```bash
         docker-compose up -d
   2. Navegar al directorio del backend:
      ```bash
         cd backend
   3. Compilar el proyecto con Maven:
         Linux/macOS:
            ```
               ./mvnw clean install
            ```
         Windows:
            ```
               ./mvnw clean install
            ```
   4. Ejecutar la aplicacion:
        Linux/macOS:
            ```
               ./mvnw spring-boot:run
            ```
         Windows:
            ```
               mvnw.cmd spring-boot:run
            ```
   API: http://localhost:8080
   Swagger UI: http://localhost:8080/swagger-ui.html


   ### Frontend (Angular)

   1. Navegar al directorio del frontend:
      ```bash
         cd frontend
   2. Instalar dependencias
      ```bash
         npm install
   3. Ejecutar el servidor de desarrollo:
      ```bash
         ng serve
   URL: http://localhost:4200


   ##  Servicios Docker

Una vez ejecutado `docker-compose up -d`, los siguientes servicios estarán disponibles:

| Servicio    | Puerto | Acceso               | Credenciales                                      |
|------------|--------|----------------------|---------------------------------------------------|
| PostgreSQL | 5433   | localhost:5433       | User: admin / Pass: admin / DB: grupo01           |
| pgAdmin    | 5050   | http://localhost:5050| Email: test@gmail.com / Pass: admin               |

### Conectar pgAdmin a PostgreSQL

1. Acceder a http://localhost:5050 e iniciar sesión.
2. Agregar nuevo servidor:
   - **Name:** volve-a-casa  
   - **Host:** db  
   - **Port:** 5432  
   - **Username / Password:** admin / admin  
   - **Database:** grupo01  

---

##  Estructura del Proyecto

   ```plaintext
   volve-a-casa/
   ├── backend/                              # Backend Spring Boot
   │   ├── src/main/java/.../
   │   │   ├── config/               # Security, Telegram, Swagger
   │   │   ├── controllers/          # REST Controllers & DTOs
   │   │   ├── persistence/          # Entities & Repositories (PostGIS)
   │   │   ├── security/             # JWT & Auth
   │   │   ├── services/             # Lógica de negocio e IA
   │   │   └── telegram/             # Bot de Telegram
   │   └── pom.xml                           # Configuración Maven
   ├── frontend/                             # Frontend Angular
   │   ├── src/app/
   │   │   ├── core/                 # Guards, Interceptors, Services
   │   │   ├── features/             # Admin, Auth, Mascota, Perfil
   │   │   └── shared/               # Componentes reutilizables
   │   └── package.json              # Dependencias npm
   ├── docker-compose.yml              # Orquestación de servicios
   └── .env                            # Variables de entorno
   ```
##  Usuario por Defecto

Al iniciar por primera vez, el `DataInitializer` crea automáticamente un administrador:

- **Email:** admin@volveacasa.com  
- **Password:** admin123  
- **Rol:** Administrador  

---

##  Funcionalidades Principales

### Gestión de Mascotas e IA
- **Registro:** Carga de fotos y descripción detallada de mascotas perdidas/encontradas.
- **Matching Inteligente:** Uso de GROQ API para comparar características y sugerir coincidencias automáticas.

### Sistema de Avistamientos y Geo
- **Geolocalización:** Reportes con mapas interactivos (Leaflet).
- **Consultas Espaciales:** Uso de PostGIS para filtrado por zona geográfica y cálculo de distancias.

### Notificaciones y Seguridad
- **Alertas:** Bot de Telegram y notificaciones por Spring Mail.
- **Seguridad:** Autenticación basada en JWT y contraseñas hasheadas con BCrypt.

---

##  Comandos Útiles

### Docker
   ```bash
   docker-compose ps
   docker-compose logs -f
   docker-compose restart
   docker-compose down -v


