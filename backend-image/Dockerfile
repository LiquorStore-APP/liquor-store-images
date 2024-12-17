# Usar una imagen base de OpenJDK
FROM openjdk:17-jdk-slim

# Establecer un directorio de trabajo
WORKDIR /app

# Copiar el archivo JAR generado al contenedor
COPY target/liquor-api-SNAPSHOT.jar app.jar

# Exponer el puerto en el que se ejecuta tu aplicación
EXPOSE 8080

# Comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]