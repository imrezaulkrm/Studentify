# Studentify Angular Frontend

Welcome to the Angular frontend of **Studentify** - an innovative Student Information Management System designed to streamline the management of student data for educational institutions.

## Overview

This Angular frontend is a crucial component of Studentify, providing a user-friendly interface for interacting with student data. It communicates with the backend built with Spring Boot to perform CRUD operations on student information stored in the MySQL database.

## Getting Started

To get started with the Angular frontend, follow these steps:

1. Clone the Studentify repository to your local machine.
2. Navigate to the `student-frontend` directory.
3. Install the necessary dependencies by running `npm install`.
4. Once the dependencies are installed, start the Angular development server by running `ng serve`.
5. Access the frontend application in your web browser at `http://localhost:4200`.

## Features

- Display all student information on the main page.
- Add new students with the "Add New Student" button.
- Update existing student information.
- Delete student records.
- Seamless navigation and intuitive user interface.

## Screenshots

Here are some screenshots of the Studentify Angular frontend:

![Home Page](https://github.com/imrezaulkrm/Studentify/raw/main/images/home-page.png)

> *Homepage of the Studentify Angular frontend.*

![Student Form Page](https://github.com/imrezaulkrm/Studentify/raw/main/images/student-page.png)

> *Adding a new student in the Studentify Angular frontend.*

![Update Page](https://github.com/imrezaulkrm/Studentify/raw/main/images/update-page.png)
> *Update student information in the Studentify Angular frontend.*

## Technologies Used

- Angular: Frontend framework for building dynamic web applications.
- Angular Material: UI component library for Angular applications.
- TypeScript: Superset of JavaScript used for Angular development.
- RxJS: Reactive Extensions library for asynchronous programming.
- Node.js and npm: JavaScript runtime and package manager for managing dependencies.

## Docker

For containerization and deployment, a Dockerfile is provided in the root directory of the project. To build and run the Docker image, follow these steps:

1. Ensure Docker is installed on your machine.
2. Open a terminal and navigate to the root directory of the project.
3. Build the Docker image with your Docker Hub username and repository name:

```bash
docker build -t your-repository-name/studentify:frontend .
```
4. Once the image is built, run the Docker container using the following command:
```bash
docker run -d -p 8080:80 --name studentify-frontend your-repository-name/studentify:frontend
```

5. Log in to Docker Hub using the following command and enter your Docker Hub credentials when prompted:
```bash
docker login
```
6. Push the Docker image to Docker Hub using the following command:
```bash
docker push your-repository-name/studentify:frontend
```
7. Logout  Docker Hub using the following command:
```bash
docker logout
```


## File Structure
student-frontend 
├── node_modules 
├── src 
│ ├── app 
│ │ ├── components 
│ │ │ ├── get-all-students 
│ │ │ │ ├── get-all-students.component.css 
│ │ │ │ ├── get-all-students.component.html 
│ │ │ │ ├── get-all-students.component.spec.ts 
│ │ │ │ └── get-all-students.component.ts 
│ │ │ ├── post-student 
│ │ │ │ ├── post-student.component.css 
│ │ │ │ ├── post-student.component.html 
│ │ │ │ ├── post-student.component.spec.ts 
│ │ │ │ └── post-student.component.ts 
│ │ │ ├── update-student 
│ │ │ │ ├── update-student.component.css 
│ │ │ │ ├── update-student.component.html 
│ │ │ │ ├── update-student.component.spec.ts 
│ │ │ │ └── update-student.component.ts 
│ │ ├── service 
│ │ │ ├── student.service.spec.ts 
│ │ │ └── student.service.ts 
│ │ ├── app.component.css 
│ │ ├── app.component.html 
│ │ ├── app.component.spec.ts 
│ │ ├── app.component.ts 
│ │ ├── app.module.ts 
│ │ └── app-routing.module.ts 
│ ├── assets 
│ ├── icon.ico 
│ ├── icon.jpg 
│ ├── index.html 
│ ├── main.ts 
│ ├── student.ico 
│ └── styles.css 
├── angular.json 
├── Dockerfile 
├── nginx.conf 
├── package.json 
├── package-lock.json 
├── tsconfig.app.json 
├── tsconfig.json 
├── tsconfig.spec.json 
└── yarn.lock
## Contributing

Contributions to Studentify are welcome! Feel free to submit bug reports, feature requests, or pull requests to help improve the project.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.
