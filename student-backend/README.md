# Studentify Spingboot Backend

Welcome to the backend of **Studentify** - an innovative Student Information Management System designed for educational institutions. This backend is built with Spring Boot to provide robust API endpoints for managing student data.

## Overview

The Studentify backend is a crucial component of the system, handling data storage, retrieval, and manipulation operations. It communicates with the frontend built with Angular to enable seamless interaction with the user interface.

## Usage

1. Clone the Studentify repository to your local machine.
2. Navigate to the `student-backend` directory.
3. Build the Spring Boot project using `./mvnw clean package`.
4. Run the application using `java -jar target/student-0.0.1-SNAPSHOT.jar`.


## Docker

For containerization and deployment, a Dockerfile is provided in the root directory of the project. To build and run the Docker image, follow these steps:

1. Ensure Docker is installed on your machine.
2. Open a terminal and navigate to the root directory of the project.
3. Build the Docker image with your Docker Hub username and repository name:

```bash
docker build -t your-repository-name/studentify:backend .
```
4.  Once the image is built, run the Docker container using the following command:
```bash
docker run -d -p 8080:8080 --name studentify-backend your-repository-name/studentify:backend 
```
5.  Log in to Docker Hub using the following command and enter your Docker Hub credentials when prompted:
```bash
docker login
``` 
6.  Push the Docker image to Docker Hub using the following command:
```bash
docker push your-repository-name/studentify:backend 
```
7.  Logout Docker Hub using the following command:
```bash
docker logout
```
8. Access the backend API endpoints at `http://localhost:8080`.

## Technologies Used

- Java
- Spring Boot
- Maven
## Project Structure

student-backend 
├── src 
│ ├── main 
│ │ ├── java/studentdot/student/ 
│ │ │ ├── controller 
│ │ │ │ └── StudentController.java 
│ │ │ ├── entity 
│ │ │ │ └── Student.java 
│ │ │ ├── repository 
│ │ │ │ └── StudentRepository.java 
│ │ │ ├── service 
│ │ │ │ └── StudentService.java 
│ │ │ └── StudentApplication.java 
│ │ ├── resources 
│ │ │ └── application.properties 
│ ├── test 
│ │ ├── java/studentdot/student/ 
│ │ │ └── StudentApplicationTests.java 
├── target 
├── Dockerfile 
├── mvnw 
├── mvnw.cmd 
└── pom.xml

**Key Components:**
- **Controller:** Handles incoming HTTP requests and delegates the processing to service classes.
- **Service:** Implements business logic and interacts with repositories.
- **Repository:** Interface for database CRUD operations.
- **Entity:** Defines JPA entities representing database tables.

## Conclusion
Studentify offers a comprehensive solution for educational institutions to manage student information efficiently. With its intuitive interface and customizable features, it streamlines data management processes, ensuring enhanced operational efficiency. From data entry facilitation to customizable security measures, Studentify meets the evolving needs of educational institutions seamlessly.

## License

This project is licensed under the MIT License - see the [LICENSE](./student-backend/LICENSE) file for details.
