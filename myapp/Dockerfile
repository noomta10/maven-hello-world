FROM eclipse-temurin:11-jre-alpine

WORKDIR /app

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY --chown=appuser:appgroup target/myapp-*.jar /app/app.jar

USER appuser

ENTRYPOINT ["java", "-jar", "/app/app.jar"]
