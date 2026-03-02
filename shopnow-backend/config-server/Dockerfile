# Stage 1: Build the application
FROM eclipse-temurin:17-jdk-jammy AS builder

WORKDIR /app
COPY . .
RUN chmod +x mvnw && ./mvnw clean package -DskipTests

# Stage 2: Run the application
FROM eclipse-temurin:17-jre-jammy

WORKDIR /app
COPY --from=builder /app/target/config-server-0.0.1-SNAPSHOT.war /app/config-server.war

EXPOSE 5859
ENTRYPOINT exec java -jar /app/config-server.war --spring.config.location=/app/src/main/resources/application.properties
