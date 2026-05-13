# 🐾 Tienda Perritos - Proyecto DevOps (EP2)

Este proyecto forma parte de la **Evaluación Parcial N°2** de la asignatura Introducción a Herramientas DevOps. Consiste en la implementación de una arquitectura de microservicios (Frontend, Backend y Base de Datos) contenedorizada con Docker y desplegada automáticamente en AWS mediante un pipeline de CI/CD.

## 🚀 Tecnologías Utilizadas
* **Contenedores:** Docker & Docker Compose
* **Cloud:** AWS (EC2, ECR, IAM)
* **CI/CD:** GitHub Actions
* **Servidor Web:** Nginx
* **Backend:** Node.js

## 🛠️ Estructura del Proyecto
* `/frontend`: Contiene el código de la interfaz de usuario y su `Dockerfile`.
* `/backend`: Lógica de negocio y conexión a base de datos.
* `/db`: Scripts de inicialización de la base de datos SQL.
* `docker-compose.yml`: Orquestación de los servicios para entorno local y despliegue.
* `.github/workflows`: Pipelines automatizados para cada servicio.

## 📦 Dockerización
Se han aplicado las siguientes buenas prácticas en los Dockerfiles:
1. **Multi-stage build:** Para reducir el tamaño de las imágenes finales.
2. **Usuario no-root:** Por seguridad, los procesos no corren con privilegios de administrador.
3. **Optimización de capas:** Orden lógico de comandos para aprovechar la caché de Docker.

## ⚙️ Pipeline CI/CD
El flujo de automatización se activa al realizar un `push` a la rama **deploy**.
1. **Build:** Construcción de la imagen Docker.
2. **Push:** Publicación de la imagen en Amazon ECR.
3. **Deploy:** Conexión SSH a la instancia EC2 para realizar un `docker pull` y reiniciar los contenedores con la nueva versión.

## 🔧 Resolución de Problemas (Troubleshooting)
Durante el desarrollo se identificaron y resolvieron los siguientes puntos críticos:
* **Configuración de Nginx:** Corrección de errores de sintaxis en `default.conf` detectados mediante `docker logs`.
* **Permisos de Docker:** Ajuste de privilegios de usuario en la instancia EC2 para permitir la ejecución de comandos sin `sudo`.
* **Autenticación ECR:** Configuración de roles IAM (`LabRole`) para permitir que la EC2 descargue imágenes de forma segura.

---
**Desarrollado por:** [Tu Nombre] & [Nombre de tu compañero]
**Institución:** Duoc UC - 2026
