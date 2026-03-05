# Stage 1: Build the jar
FROM maven:3.8.6-eclipse-temurin-11 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Run the jar
FROM eclipse-temurin:11
VOLUME /tmp
EXPOSE 8081
COPY --from=builder /app/target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
