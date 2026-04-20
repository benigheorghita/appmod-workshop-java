# syntax=docker/dockerfile:1
FROM maven:3.9.11-eclipse-temurin-8 AS build
WORKDIR /workspace

# Cache dependencies first, then copy sources.
COPY pom.xml ./
COPY web/pom.xml web/pom.xml
COPY worker/pom.xml worker/pom.xml
RUN mvn -B -q -pl web -am dependency:go-offline

COPY web/src web/src
RUN mvn -B -q -pl web -am -DskipTests package

FROM eclipse-temurin:8-jre
WORKDIR /app
COPY --from=build /workspace/web/target/assets-manager-web-*.jar app.jar

RUN useradd --system --create-home --uid 10001 appuser
USER appuser

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/app.jar"]

