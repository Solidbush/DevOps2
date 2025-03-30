FROM eclipse-temurin:17-alpine

WORKDIR /app

RUN apk add --no-cache git maven

RUN apk add --no-cache git && \
    git clone https://gitlab.com/deusops/projects/react-spring-app.git /app && \
    cd /app/spring-backend

WORKDIR /app/spring-backend
RUN mvn clean install

CMD ["java", "-jar", "target/*.jar"]