# Stage 1: Build the application
FROM eclipse-temurin:17-jdk-jammy AS builder

WORKDIR /app
COPY . .
RUN chmod +x mvnw && ./mvnw clean package -DskipTests

# Stage 2: Run the application
FROM eclipse-temurin:17-jre-jammy

WORKDIR /app
COPY --from=builder /app/target/shopping-cart-service-0.0.1-SNAPSHOT.war /app/cart-service.war

EXPOSE 5863
ENTRYPOINT exec java -jar /app/cart-service.war --spring.config.location=/app/src/main/resources/application.properties
