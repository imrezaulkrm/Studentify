## Kubernetes Deployment

This directory contains Kubernetes deployment files for deploying the Studentify application on a Kubernetes cluster. Below are the details of each file:

- **angular-deployment.yml:** Kubernetes deployment configuration for the Angular frontend of the Studentify application.

- **ingress.yml:** Kubernetes Ingress configuration for routing incoming traffic to the appropriate services.

- **mysql-configmap.yml:** Kubernetes ConfigMap for storing MySQL configuration settings.

- **mysql-deployment.yml:** Kubernetes deployment configuration for the MySQL database.

- **mysql-pv.yml:** Kubernetes PersistentVolume (PV) configuration for MySQL data storage.

- **mysql-pvc.yml:** Kubernetes PersistentVolumeClaim (PVC) configuration for MySQL data storage.

- **mysqldb-credentials.yml:** Kubernetes Secret for storing MySQL database credentials securely.

- **springboot-deploy.yml:** Kubernetes deployment configuration for the Spring Boot backend of the Studentify application.

- **storage-class.yml:** Kubernetes StorageClass configuration for dynamically provisioning storage.

### Deployment Process

To deploy the Studentify application on Kubernetes using these files, follow these steps:

1. Make sure you have a Kubernetes cluster configured and kubectl installed on your machine.

2. Navigate to the Kubernetes folder in the project directory.

3. Apply the Kubernetes resources using kubectl apply:
```bash
   kubectl apply -f angular-deployment.yml
   kubectl apply -f ingress.yml
   kubectl apply -f mysql-configmap.yml
   kubectl apply -f mysql-deployment.yml
   kubectl apply -f mysql-pv.yml
   kubectl apply -f mysql-pvc.yml
   kubectl apply -f mysqldb-credentials.yml
   kubectl apply -f springboot-deploy.yml
   kubectl apply -f storage-class.yml
```
4. Verify that all resources are created successfully:

```bash
kubectl get pods
kubectl get services
kubectl get ingresses
```
5. Access the application using the Ingress address provided by your Kubernetes cluster.

## Using DockerHub Images

By default, these deployment files reference DockerHub images. If you've pushed your images to DockerHub, update the image references in the deployment files accordingly.

## Conclusion 
In conclusion, Studentify offers a versatile platform to meet the evolving demands of educational institutions. Whether it's facilitating data entry, ensuring data security, or enabling customization to meet specific institutional needs, Studentify provides a comprehensive solution for managing student information effectively.

## License 
This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details. You can copy and paste this section into your README.md file in the Kubernetes folder of your project repository. Let me know if you need further assistance!
