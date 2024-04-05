# Use an appropriate base image that includes Java and Maven
FROM maven:3.8.4-openjdk-17-slim AS builder

# Copy the project files into the container
COPY . /app

# Set the working directory
WORKDIR /app

# Build the application with Maven
RUN mvn -B package --file pom.xml

# Create a final image for running the application
FROM tomcat:9.0.56-jdk17-openjdk-slim

# Copy the WAR file built in the previous stage to the Tomcat webapps directory
COPY --from=builder /app/target/*.war /usr/local/tomcat/webapps/
