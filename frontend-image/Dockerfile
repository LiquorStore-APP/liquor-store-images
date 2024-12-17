# Usar la imagen base de Node.js
FROM node:20.11.1

# Crear el directorio de la app en el contenedor
RUN mkdir -p /app

# Establecer /app como el directorio de trabajo
WORKDIR /app

# Instalar Angular CLI globalmente
RUN npm install -g @angular/cli@18.2.4

# No copiar archivos ni ejecutar npm install porque el proyecto aún no está disponible

# Comando por defecto al iniciar el contenedor
CMD ["/bin/sh"]