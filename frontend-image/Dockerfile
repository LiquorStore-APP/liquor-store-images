# Base image
FROM node:14-alpine

# Establece el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copia los archivos necesarios al contenedor
COPY package*.json ./
RUN npm install

# Copia la carpeta dist/ del proyecto Angular al contenedor
COPY dist/ ./dist/

# Expose the port the application runs on
EXPOSE 4200

# Comando para iniciar la aplicación
CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "4200"]