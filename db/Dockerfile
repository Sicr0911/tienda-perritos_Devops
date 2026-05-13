# Usamos la imagen oficial de MySQL (la versión 8.0 es muy estable)
FROM mysql:8.0

# Copiamos nuestro script al directorio de inicialización automática de MySQL
COPY init.sql /docker-entrypoint-initdb.d/

# Exponemos el puerto por defecto de MySQL
EXPOSE 3306