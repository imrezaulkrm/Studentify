# Student Information Management System (Studentify)

**Studentify** is an innovative Student Information Management System designed to streamline the management of student data for educational institutions. Built with Angular for the frontend, Spring Boot for the backend, and MySQL for the database, Studentify offers a seamless user experience and robust functionality. The system comprises three main pages, with the first page displaying all student information. This page features convenient buttons such as "Add New Student" to facilitate easy data entry. Upon clicking the "Add New Student" button, users are directed to a student form where they can input new student details. After submission, users are redirected back to the first page, now updated with the newly added student information. Each student entry on this page includes options to delete or update the information. Clicking "Delete" removes the student's data from the system, while selecting "Update" opens a separate form page for modifying the student's details. This intuitive interface and efficient workflow make Studentify a valuable tool for managing student information effectively within educational institutions.

![Home Page](https://github.com/imrezaulkrm/Studentify/raw/main/images/home-page.png)

![Student Form Page](https://github.com/imrezaulkrm/Studentify/raw/main/images/student-page.png)

![Update Page](https://github.com/imrezaulkrm/Studentify/raw/main/images/update-page.png)


## Table of Contents
- [Project Structure](#project-structure)
- [Dockerization](#dockerization)
  - [Dockerfile For Backend](#dockerfile-for-backend)
  - [Dockerfile For Fontend](#dockerfile-for-fontend)
  - [Docker Compose File for Backend, Frontend, and MySQL](#docker-compose-file-for-backend-frontend-and-mysql)
- [Accessing The Application](#accessing-the-application)
- [Conclusion](#conclusion)
- [License](#license)

## Project Structure
```bash
├── images
├── student-backend
│   ├── src
│   │   ├── main
│   │   │   ├── java/studentdot/student/
│   │   │   │   ├── controller
│   │   │   │   │   └── StudentController.java
│   │   │   │   ├── entity
│   │   │   │   │   └── Student.java
│   │   │   │   ├── repository
│   │   │   │   │   └── StudentRepository.java
│   │   │   │   ├── service
│   │   │   │   │   └── StudentService.java
│   │   │   │   └── StudentApplication.java
│   │   │   ├── resources
│   │   │   │   ├── static
│   │   │   │   ├── templates
│   │   │   │   └── application.properties
│   │   ├── test
│   │   │   ├── java/studentdot/student/
│   │   │   │   └── StudentApplicationTests.java
│   ├── target
│   ├── Dockerfile
│   ├── mvnw
│   ├── mvnw.cmd
│   └── pom.xml
├── student-fontend
│   ├── node_modules
│   ├── src
│   │   ├── app
│   │   │   ├── components
│   │   │   │   ├── get-all-students
│   │   │   │   │   ├── get-all-students.component.css
│   │   │   │   │   ├── get-all-students.component.html
│   │   │   │   │   ├── get-all-students.component.spec.ts
│   │   │   │   │   └── get-all-students.component.ts
│   │   │   │   ├── post-student
│   │   │   │   │   ├── post-student.component.css
│   │   │   │   │   ├── post-student.component.html
│   │   │   │   │   ├── post-student.component.spec.ts
│   │   │   │   │   └── post-student.component.ts
│   │   │   │   ├── update-student
│   │   │   │   │   ├── update-student.component.css
│   │   │   │   │   ├── update-student.component.html
│   │   │   │   │   ├── update-student.component.spec.ts
│   │   │   │   │   └── update-student.component.ts
│   │   │   ├── service
│   │   │   │   ├── student.service.spec.ts
│   │   │   │   └── student.service.ts
│   │   │   ├── app.component.css
│   │   │   ├── app.component.html
│   │   │   ├── app.component.spec.ts
│   │   │   ├── app.component.ts
│   │   │   ├── app.module.ts
│   │   │   └── app-routing.module.ts
│   │   ├── assets
│   │   ├── icon.ico
│   │   ├── icon.jpg
│   │   ├── index.html
│   │   ├── main.ts
│   │   ├── student.ico
│   │   └── styles.css
│   ├── angular.json
│   ├── Dockerfile
│   ├── nginx.conf
│   ├── package.json
│   ├── package-lock.json
│   ├── tsconfig.app.json
│   ├── tsconfig.json
│   ├── tsconfig.spec.json
│   └── yarn.lock
└── docker-compose.yml
```
Briefly describe the purpose of each main directory in your project.

## Dockerization
The project consists of two Dockerfiles, one for the frontend and the other for the backend. These Dockerfiles define the build and runtime environments for each component. Additionally, a Docker Compose file orchestrates the integration of both components, streamlining development and deployment processes.

### Dockerfile For Backend

To create a Dockerfile for the backend service located at `/student-backend`, navigate to the project root directory and create a Dockerfile with the following content:

```dockerfile
# Use OpenJDK as the base image for building
FROM openjdk:17 AS builder

# Set working directory
WORKDIR /app

# Copy Maven Wrapper
COPY mvnw .
COPY mvnw.cmd .
COPY .mvn .mvn

# Copy Maven project files
COPY pom.xml .

# Copy source code
COPY src ./src

# Build Spring Boot application
RUN ./mvnw package -DskipTests

# Use OpenJDK as the base image for running the application
FROM openjdk:17

# Set working directory
WORKDIR /app

# Copy the built JAR file from the previous stage
COPY --from=builder /app/target/student-0.0.1-SNAPSHOT.jar app.jar

# Expose port
EXPOSE 8080

# Run the Spring Boot application
CMD ["java", "-jar", "app.jar"]
```

### Dockerfile For Fontend

To create a Dockerfile for the backend service located at `/student-fontend`, navigate to the project root directory and create a Dockerfile with the following content:
```dockerfile
# Stage 1: Build the application
FROM node:alpine as build

# Set working directory for the build stage
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./# Stage 1: Build the application
FROM node:alpine as build

# Set working directory for the build stage
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .

# Build the application
RUN npm run build

# Stage 2: Create the production image
FROM nginx:alpine

# Copy built files from the build stage
COPY --from=build /usr/src/app/dist/student-fontend /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf


# Expose port
EXPOSE 80

# Command to run NGINX in the foreground
CMD ["nginx", "-g", "daemon off;"]

# Copy application code
COPY . .

# Build the application
RUN npm run build

# Stage 2: Create the production image
FROM nginx:alpine

# Copy built files from the build stage
COPY --from=build /usr/src/app/dist/student-fontend /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf


# Expose port
EXPOSE 80

# Command to run NGINX in the foreground
CMD ["nginx", "-g", "daemon off;"]
```

### Docker Compose File for Backend, Frontend, and MySQL
Below is a Docker Compose file (`docker-compose.yml`) orchestrating services for MySQL, backend, and frontend components:

```yaml
version: '3.8'

services:
  mysql:
    image: mysql:latest
    container_name: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: Rez@ul123
      MYSQL_DATABASE: studentdb
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

  backend:
    build:
      context: .
      dockerfile: ./student-backend
    container_name: backend
    restart: always
    environment:
      SPRING_PROFILES_ACTIVE: dev
      SPRING_DATASOURCE_URL: jdbc:mysql://mysql:3306/studentdb
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD: Rez@ul123
    ports:
      - "8080:8080"
    depends_on:
      - mysql

  frontend:
    build:
      context: .
      dockerfile: ./student-frontend
    container_name: frontend
    restart: always
    ports:
      - "80:80"

volumes:
  mysql_data:
```

**Run Docker Compose**: Run the following command to start the services defined in your `docker-compose.yml` file:
```docker
docker-compose up -d
```
**Stop Services**: When you're done testing or working with your application, you can stop the Docker containers by running:
```docker
docker-compose down
``` 
This command will stop and remove the containers defined in your `docker-compose.yml` file.
    

That's it! You've successfully run your full project using Docker Compose.
## Accessing The Application

Access the running application in a web browser at 
```
http://localhost:80
```

##   Conclusion

In conclusion, the Student Information Management System (Studentify) provides a robust solution for educational institutions to efficiently manage student data. Leveraging Angular for the frontend and Spring Boot for the backend, along with MySQL as the database, the system offers a user-friendly interface and seamless workflow for administrators. With features like adding, updating, and deleting student records, Studentify empowers institutions to maintain accurate and up-to-date student information. Dockerization further simplifies deployment, allowing for easy setup and scalability. Overall, Studentify stands as a comprehensive tool to streamline student information management, enhancing organizational efficiency and effectiveness.

## License

This project is licensed under the MIT License. Feel free to use, modify, and distribute it as per the terms of the license.
