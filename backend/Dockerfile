# --- ETAPA 1: Construcción (Builder) ---
FROM node:18-alpine AS builder
WORKDIR /app

# Copiamos solo los archivos de dependencias primero para aprovechar la caché de Docker
COPY package*.json ./
RUN npm install

# Copiamos el resto del código fuente
COPY . .

# --- ETAPA 2: Producción (Imagen final liviana y segura) ---
FROM node:18-alpine
WORKDIR /app

# Copiamos los archivos ya procesados desde la etapa 'builder'
COPY --from=builder /app ./

# Cambiamos al usuario 'node' (viene por defecto en la imagen) para no ser root
USER node

# Exponemos el puerto que configuraste en el server.js (3001)
EXPOSE 3001

# Comando para iniciar la aplicación
CMD ["node", "server.js"]