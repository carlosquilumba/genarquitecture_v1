# GenArquitecture - Generador de Arquitecturas

## Descripción

GenArquitecture es una aplicación que facilita la generación de arquitecturas de software, utilizando un backend para la lógica de procesamiento y un frontend para la interacción del usuario. Este proyecto utiliza Docker Compose para orquestar sus servicios.

## Requisitos

Antes de comenzar, asegúrate de tener instalado lo siguiente:

*   **Docker**: [Instalar Docker](https://docs.docker.com/get-docker/)
*   **Docker Compose**: Generalmente viene incluido con las instalaciones modernas de Docker Desktop.

## Configuración y Ejecución

Sigue estos pasos para poner en marcha la aplicación:

1.  **Clonar el Repositorio (o descargar los archivos)**:
    Si tienes un repositorio Git, clónalo:
    ```bash
    git clone <URL_DE_TU_REPOSITORIO>
    cd genarquitecture
    ```
    Si solo compartes los archivos, asegúrate de tener `docker-compose.yml` y `.env.example` en el mismo directorio.

2.  **Configurar Variables de Entorno**:
    Copia el archivo de ejemplo `.env.example` a `.env`:
    ```bash
    cp .env.example .env
    ```
    Abre el archivo `.env` recién creado y rellena las variables necesarias con tus propias credenciales y configuraciones (especialmente las de Azure OpenAI y Minio).

3.  **Iniciar la Aplicación**:
    Desde el directorio raíz del proyecto, ejecuta Docker Compose para construir (si es necesario) y levantar todos los servicios:
    ```bash
    docker compose up -d
    ```
    El flag `-d` ejecuta los contenedores en segundo plano.

## Acceso a la Aplicación

Una vez que los servicios estén en funcionamiento:

*   **Frontend**: Accede a la interfaz de usuario en `http://localhost:3000`
*   **Backend API**: La API del backend estará disponible en `http://localhost:5000`
*   **Minio Console**: La consola de Minio estará disponible en `http://localhost:9001` (usa las credenciales `MINIO_ROOT_USER` y `MINIO_ROOT_PASSWORD` de tu archivo `.env`).

## Detener la Aplicación

Para detener y eliminar los contenedores (pero mantener los volúmenes de datos):

```bash
docker compose down
```

Para detener y eliminar los contenedores y todos los volúmenes de datos (¡cuidado, esto eliminará los datos de Minio!):

```bash
docker compose down -v
```

## Variables de Entorno (`.env`)

Asegúrate de configurar las siguientes variables en tu archivo `.env`:

*   `AZURE_OPENAI_DEPLOYMENT_NAME`: Nombre de tu despliegue de Azure OpenAI.
*   `AZURE_OPENAI_API_KEY`: Tu clave de API de Azure OpenAI.
*   `AZURE_OPENAI_API_BASE`: La URL base de tu instancia de Azure OpenAI.
*   `MINIO_ENDPOINT`: Endpoint de Minio (por defecto `http://minio:9000` si se ejecuta con Docker Compose).
*   `MINIO_ACCESS_KEY`: Clave de acceso para Minio.
*   `MINIO_SECRET_KEY`: Clave secreta para Minio.
*   `MINIO_BUCKET`: Nombre del bucket de Minio a utilizar.
*   `MINIO_ROOT_USER`: Usuario root para la consola de Minio (por defecto `minioadmin`).
*   `MINIO_ROOT_PASSWORD`: Contraseña root para la consola de Minio (por defecto `minioadmin`).
*   `WORD_TEMPLATE_PATH`: Ruta a la plantilla de Word dentro del contenedor (generalmente no necesita cambiarse).
*   `SKILLS_DIR`: Directorio de habilidades dentro del contenedor (generalmente no necesita cambiarse).

---