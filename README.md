# Práctico Integrador: Git + Docker + Aplicación Contenerizada

Esta es una aplicación web de demostración construida con **Express.js**, el framework minimalista para Node.js. El proyecto está configurado para ser ejecutado tanto en un entorno de desarrollo local como en un contenedor de Docker para producción.

## Prerrequisitos

Antes de comenzar, asegúrate de tener instalado el siguiente software:

*   **Node.js**: Se recomienda la versión **18.x** o superior.
*   **NPM**: El gestor de paquetes de Node.js (se instala con Node.js).
*   **Docker**: Opcional, pero recomendado para un entorno de producción consistente.

## Instalación

1.  **Clona el repositorio** en tu máquina local.

2.  **Navega al directorio del proyecto** y abre una terminal:
    ```bash
    cd ruta/a/tu/proyecto/ISTEA
    ```

## Cómo Ejecutar la Aplicación

Puedes ejecutar el proyecto de dos maneras:

### 1. Modo Desarrollo (usando Node.js)

Este método es ideal para desarrollar y probar cambios rápidamente.

```bash
# Instala las dependencias del proyecto
npm install

# Inicia el servidor de desarrollo
npm start
```

La aplicación estará disponible en [http://localhost:3000](http://localhost:3000).

### 2. Modo Producción (usando Docker)

Este método empaqueta la aplicación en un contenedor portable y optimizado, ideal para el despliegue.

```bash
# 1. Construye la imagen de Docker
# El tag "-t istea-app" le da un nombre a tu imagen.
docker build -t istea-app .

# 2. Ejecuta el contenedor a partir de la imagen
# -p 3000:3000 mapea el puerto de tu máquina al del contenedor.
# -d lo ejecuta en segundo plano.
docker run -p 3000:3000 -d --name istea-container istea-app
```

La aplicación estará disponible en [http://localhost:3000](http://localhost:3000).

#### Comandos útiles de Docker

*   **Ver logs de la aplicación**: `docker logs istea-container`
*   **Detener el contenedor**: `docker stop istea-container`
*   **Ver contenedores en ejecución**: `docker ps`

## Estructura del Proyecto

```
├── bin/
│   └── www           # Script de inicio del servidor HTTP
├── public/           # Archivos estáticos (CSS, JS, imágenes)
├── routes/           # Manejadores de rutas (index.js, users.js)
├── views/            # Plantillas de la interfaz (archivos .jade)
├── .dockerignore     # Archivos a ignorar por Docker
├── app.js            # Archivo principal de configuración de Express
├── Dockerfile        # Instrucciones para construir la imagen de Docker
├── package.json      # Metadatos y dependencias del proyecto
└── README.md         # Esta documentación
```