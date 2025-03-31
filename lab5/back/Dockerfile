FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

RUN apk add --no-cache git maven && \
    git clone --depth 1 --branch main https://gitlab.com/deusops/projects/react-spring-app.git /repo && \
    mv /repo/spring-backend/* /app/ && \
    rm -rf /repo && \
    mvn clean package -DskipTests && \
    mv /app/target/*.jar /app/app.jar && \
    rm -rf /app/target ~/.m2

RUN addgroup -S appgroup && adduser -S appuser -G appgroup && \
    mkdir -p /app/data && \
    chown -R appuser:appgroup /app

USER appuser

EXPOSE 8080

CMD ["java", "-jar", "/app/app.jar"]