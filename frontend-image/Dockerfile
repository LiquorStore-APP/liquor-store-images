# Etapa 1: Construcción
FROM node:20.17.0-alpine AS build

# Establece el directorio de trabajo en el contenedor
RUN mkdir /app
WORKDIR /app

#ARG VOLUME_FRONTEND_PATH
#ENV VOLUME_FRONTEND_PATH ${VOLUME_FRONTEND_PATH}
COPY liquor-store-web /app/

# Instala Angular CLI globalmente
RUN npm install -g @angular/cli

# Instala las dependencias
RUN npm install

# Construye la aplicación Angular
RUN ng build --configuration=production

# Etapa 2: Servidor web para servir la aplicación
FROM nginx:1.25.2-alpine

# Instalar bash
RUN apk add --no-cache bash

# Copiar los archivos de la build desde la etapa anterior
COPY --from=build /app/dist/liquor-store-web/browser/ /usr/share/nginx/html

# Eliminar configuración por defecto de Nginx si no la necesitas
RUN rm /etc/nginx/conf.d/default.conf

# Configurar un archivo de configuración personalizado para Nginx
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expone el puerto 80 para el contenedor
EXPOSE 80

# Comando por defecto para iniciar Nginx
CMD ["nginx", "-g", "daemon off;"]
