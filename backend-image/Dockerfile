# Etapa 1: Construcción
FROM maven:3.8.5-openjdk-17 AS builder

# Establece el directorio de trabajo en el contenedor
WORKDIR /app

# Copia el archivo pom.xml y las dependencias
COPY liquor-store-api/pom.xml .

# Descarga las dependencias necesarias
RUN mvn dependency:go-offline -B

# Copia el código fuente del proyecto
COPY liquor-store-api/src ./src

# Compila el proyecto y genera el .jar
RUN mvn clean package -DskipTests

# Etapa 2: Ejecución
FROM openjdk:17-jdk-slim

# Establece el directorio de trabajo
WORKDIR /app

# Copia el archivo JAR generado desde la etapa de construcción
COPY --from=builder /app/target/*.jar app.jar

# Expone el puerto en el que corre la aplicación
EXPOSE 8080

# Comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]