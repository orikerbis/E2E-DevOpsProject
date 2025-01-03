# E2E-DevOpsProject

## Description
E2E-DevOpsProject demonstrates the entire process of deploying an application using modern DevOps practices. The project showcases an **Employee Management System** application, built with a **Node.js backend**, **React frontend**, and **AWS RDS MySQL database**. It includes directories for **applications**, **infrastructure**, and **GitOps**, along with a fully integrated CI/CD pipeline for seamless deployments.

The live application is available at: [app.kerbis.online](https://app.kerbis.online)

---

## Project Structure
The project is organized into the following main directories:

1. **Applications Directory**:
   - Contains the application code (frontend, backend).
   - Includes a Helm chart for Kubernetes deployments.
   - Implements a CI/CD pipeline file under the `.github/workflows` directory:
     - Builds Docker images.
     - Pushes images to **AWS ECR**.
     - Updates the image tag in the GitOps repository.

2. **Infrastructure Directory**:
   - `modules` directory contains a main module named **platform**:
     - Defines the infrastructure including **EKS**, **VPC**, **RDS**, and other AWS components.
   - `environment` directory includes a `main.tf` file:
     - Runs the `platform` module with environment-specific variables.

3. **GitOps Directory**:
   - `environments` directory contains environment-specific values files.
   - `application-dev` file in the root points to the application Helm chart for the development branch.
   - Changes to values files (e.g., image tags) automatically trigger **ArgoCD** for deployment updates.

---

## Features
- **Full-Stack Employee Management System**:
  - Backend: Node.js.
  - Frontend: React.
  - Database: AWS RDS MySQL.

- **CI/CD Pipeline**:
  - Automated build, test, and deployment using GitHub Actions.
  - Docker images are pushed to AWS ECR.
  - Helm charts are updated with the new image tag in the GitOps repository.

- **Infrastructure as Code (IaC)**:
  - Modular Terraform setup for creating AWS resources.
  - EKS cluster, VPC, RDS, and other necessary components.

- **GitOps with ArgoCD**:
  - Automatically applies changes to Kubernetes deployments based on updates in the values file.

---

## Installation

### Prerequisites
- **Node.js** and **npm** installed.
- **Terraform** installed.
- Access to **AWS** account with necessary permissions.
- **kubectl** and **Helm** installed for Kubernetes management.
- **ArgoCD** configured in your cluster.

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/E2E-DevOpsProject.git
   cd E2E-DevOpsProject
