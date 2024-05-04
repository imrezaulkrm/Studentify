# Student Information Management System (Studentify)

**Studentify** is an innovative Student Information Management System designed for educational institutions. It's built with Angular, Spring Boot, and MySQL for a seamless user experience. The system includes three main pages, with the first displaying all student information. Convenient buttons like "Add New Student" streamline data entry. Upon submission, users are redirected to an updated page. Each entry allows for easy deletion or updating. "Delete" removes data, while "Update" opens a modification form. Studentify's intuitive interface and efficient workflow make it indispensable for educational data management.

## Workflow Diagram

![enter image description here](https://github.com/imrezaulkrm/Studentify/raw/main/images/diagram.png)
## Project Details
### Branches:
-   ***Main Branch***: Contains configuration files like Kubernetes manifests.
-   ***Frontend Branch***: Contains all frontend files.
-   ***Backend Branch***: Contains all backend files.

### Technologies Used:
- Angular 16
- Spring Boot
- MySQL

### Functionality:
- CRUD Operations for Student Information

### Deployment:
- Dockerized for seamless deployment
- Orchestrated deployment using Kubernetes with Minikube
- Utilized deployment objects such as Deployment, Service, PV, PVC, ConfigMap, Secret, and StorageClass
- Integrated Ingress for efficient routing of incoming traffic

### Customization Options:
- Role-based access control for different user levels
- Customizable data fields for specific educational institution requirements
- Integration with third-party APIs for additional functionality (e.g., payment processing, student communication)
- Localization and multi-language support for international users
- Customizable dashboard and reporting features for administrators

## CI/CD

#### Continuous Integration (CI):

-   Utilized Jenkins for CI purposes
-   Configured Jenkins Multibranch Pipeline to automatically build and test branches
-   Integrated with version control system to trigger builds upon code changes
-   Implemented automated testing to ensure code quality and reliability

#### Continuous Deployment (CD):

-   Implemented CD using ArgoCD for Kubernetes deployments
-   Configured ArgoCD to automatically synchronize Kubernetes manifests with Git repositories
-   Enabled automatic rollouts and rollbacks based on changes to the Git repository
-   Ensured smooth and reliable deployment of new versions without manual intervention
## Conclusion 
In conclusion, Studentify provides a comprehensive solution for educational institutions to efficiently manage student information. With its user-friendly interface, robust functionality, and customizable options, Studentify empowers institutions to streamline their data management processes and enhance operational efficiency. Whether it's facilitating data entry, ensuring data security, or enabling customization to meet specific institutional needs, Studentify offers a versatile platform to meet the evolving demands of educational institutions.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.