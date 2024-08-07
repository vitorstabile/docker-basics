# Use an official Maven image with OpenJDK 18 to build the application
FROM maven:3.8.6-openjdk-18-slim AS build

# Set the working directory in the container
WORKDIR /home/app

# Copy the pom.xml to source code into the container
COPY ./pom.xml /home/app/pom.xml

# Copy the SpringBoot application entry point class (This not change in spring boot application)
COPY ./src/main/java/com/dockerexample/test/TestApplication.java /home/app/src/main/java/com/dockerexample/test/TestApplication.java

# Package the application
RUN mvn -f /home/app/pom.xml clean package

# Copy the source code into the container again
COPY . /home/app

# Package the application again. This will not take so long
RUN mvn -f /home/app/pom.xml clean package

# Use the same OpenJDK 18 runtime as a parent image
FROM openjdk:18.0-slim

# Copy the JAR file from the build stage to the runtime stage
COPY --from=build /home/app/target/*.jar app.jar

# Expose the port the application runs on
EXPOSE 5000

# Run the Spring Boot application
ENTRYPOINT [ "sh", "-c", "java -jar /app.jar" ]