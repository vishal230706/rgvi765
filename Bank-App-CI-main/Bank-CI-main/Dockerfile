# Stage 1: Build the application using Maven and JDK 17
FROM maven:3.9-eclipse-temurin-21 AS builder
WORKDIR /build
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Run the application
FROM eclipse-temurin:21-jdk-alpine
ENV APP_HOME=/usr/src/app
WORKDIR $APP_HOME
COPY --from=builder /build/target/*.jar $APP_HOME/app.jar
EXPOSE 8080
CMD ["java", "-jar", "app.jar"]
