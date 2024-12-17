# Etapa 1: Construcción
FROM node:20-alpine AS build

# Establecer el directorio de trabajo en el contenedor
WORKDIR /app

# Copiar los archivos del proyecto Angular al contenedor
COPY package*.json ./

# Instalar las dependencias de Node.js
RUN npm install

# Copiar el resto de los archivos del proyecto
COPY . .

# Construir la aplicación Angular
RUN npm run build --prod

# Etapa 2: Servir la aplicación con Angular CLI (sin Nginx)
FROM node:20-alpine

# Establecer el directorio de trabajo en el contenedor
WORKDIR /app

# Copiar los archivos construidos desde la etapa anterior al contenedor
COPY --from=build /app/dist/liquid-store-web /app/dist/liquid-store-web

# Instalar Angular CLI en el contenedor
RUN npm install -g @angular/cli

# Exponer el puerto que Angular usa por defecto (4200)
EXPOSE 4200

# Comando para iniciar el servidor de desarrollo de Angular
CMD ["ng serve", "--host", "0.0.0.0", "--port", "4200"]