# Usamos una imagen de Nginx muy ligera y rápida
FROM nginx:alpine

# Copiamos tu configuración personalizada de Nginx
# Esto es clave para que Nginx sepa cómo manejar las rutas y conectarse con tu backend
COPY default.conf /etc/nginx/conf.d/default.conf

# Copiamos los archivos de tu página web al directorio público de Nginx
COPY index.html /usr/share/nginx/html/
COPY app.js /usr/share/nginx/html/

# Exponemos el puerto 80 (el estándar para tráfico web HTTP)
EXPOSE 80   

# (No hace falta poner un CMD, la imagen de Nginx ya arranca el servidor automáticamente)