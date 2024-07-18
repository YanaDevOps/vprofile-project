# Stage 1: Build the application with Maven
FROM openjdk:11-jdk AS build
RUN apt-get update && apt-get install -y maven git

# Clone the repository and build the application
RUN git clone --branch docker https://github.com/YanaDevOps/vprofile-project.git
WORKDIR vprofile-project
RUN mvn clean install

# Stage 2: Deploy the application to Tomcat
FROM tomcat:9-jre11
LABEL Project="Vprofile"
LABEL Author="Yana"

# Remove default webapps
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy the built WAR file from the previous stage
COPY --from=build /vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

# Expose port 8080
EXPOSE 8080

# Start Tomcat server
CMD ["catalina.sh", "run"]

