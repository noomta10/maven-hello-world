# Stage 1: Build
FROM maven:3.8.6-eclipse-temurin-11 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package

# Stage 2: Run
FROM eclipse-temurin:11-jre-alpine
WORKDIR /app

# Create a non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

# Copy the artifact from the builder stage
COPY --from=builder /app/target/my-app-*.jar /app/app.jar

ENTRYPOINT ["java", "-jar", "/app/app.jar"]
