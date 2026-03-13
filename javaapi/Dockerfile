FROM eclipse-temurin:8u392-b08-jdk AS build
WORKDIR /app
RUN apt update && apt install maven -y
COPY . .
RUN mvn package -DskipTests
 
FROM eclipse-temurin:8-jdk
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 9000
ENTRYPOINT ["java", "-jar", "app.jar"]
