FROM maven:3.8.6-openjdk-8 AS builder
WORKDIR /app
COPY pom.xml .
COPY .mvn ./mvn
COPY src ./src
RUN mvn package -DskipTests

FROM openjdk:8-jdk-slim
WORKDIR /app
COPY --from=builder /app/target/*.jar ./users-api.jar
EXPOSE 8083
CMD ["java", "-jar", "users-api.jar"]
