# E2E-DevOpsProject
**Note:** The original project is divided into three repositories: one for the application code + Helm Chart, one for the infrastructure code, and another for the GitOps directories. This repository combines all components for convenience and ease of use.

## Description
E2E-DevOpsProject demonstrates the entire process of deploying an application using modern DevOps practices. The project showcases an Employee Management System application, built with a Node.js backend, React frontend, and AWS RDS MySQL database. It includes directories for applications, infrastructure, and GitOps, along with a fully integrated CI/CD pipeline for seamless deployments.

This project emphasizes establishing a robust and automated development environment, ensuring that changes are tested and deployed efficiently while maintaining consistency. The live application is available at: [app.kerbis.online](https://app.kerbis.online)

## Project Structure
The project is organized into the following main directories:

1. **Applications Directory**:
   - Contains the application code (frontend, backend).
   - Includes a Helm chart for Kubernetes deployments.
   - Implements a CI/CD pipeline file under the `.github/workflows` directory:
     - Builds Docker images.
     - Pushes images to **AWS ECR**.
     - Updates the image tag in the GitOps repository.
   - The application directory also includes a `docker-compose` file for running the application locally.

2. **Infrastructure Directory**:
   - **Terraform** for Infrastructure as Code (IaC).
   - `modules` directory contains a main module named **platform**:
     - Defines the infrastructure including **EKS**, **VPC**, **RDS**, and other AWS components.
     - Includes **Karpenter** for cluster autoscaling.
   - `environment` directory includes a `main.tf` file:
     - Runs the `platform` module with environment-specific variables.

3. **GitOps Directory**:
   - `environments` directory contains environment-specific values files.
   - `application-dev` file in the root points to the application Helm chart for the development branch.
   - Changes to values files (e.g., image tags) automatically trigger **ArgoCD** for deployment updates.

---

## Features

### Full-Stack Employee Management System
- **Backend**: Node.js.
- **Frontend**: React.
- **Database**: AWS RDS MySQL.

### CI/CD Pipeline
- Automated build, test, and deployment using GitHub Actions.
- Docker images are pushed to AWS ECR.
- Helm charts are updated with the new image tag in the GitOps repository.

### Infrastructure as Code (IaC)
- Modular Terraform setup for creating AWS resources.
- Includes EKS cluster, VPC, RDS, and other necessary components.
- **Cluster Autoscaling** with **Karpenter**:
  - Karpenter is deployed using Terraform to ensure efficient scaling of EKS clusters based on workloads.
  - Automatically provisions and scales nodes to match the demands of the application.

### Monitoring and Logging
- **Prometheus and Grafana** for application and infrastructure monitoring:
  - Prometheus is used for collecting and storing metrics.
  - Grafana is used for visualizing metrics and creating dashboards for real-time monitoring.
- **Loki** for log visualization:
  - Centralized logging solution integrated with Grafana.
  - Allows developers to query, filter, and analyze logs for debugging and monitoring purposes.

### External Secrets Integration
- **External Secrets** are used for managing sensitive information like database passwords and hosts.
- The **External Secret** Helm chart is deployed using Terraform.
- Integrates with the `ClusterStore` resource in the application Helm chart and the `ExternalSecret` resource.
- Credentials are securely retrieved from **AWS Secrets Manager**.

### GitOps with ArgoCD
- Automatically applies changes to Kubernetes deployments based on updates in the values file.

---

## License
This project is licensed under the MIT License.

## Contact
For questions or feedback, please reach out to [orikerbis@gmail.com].
