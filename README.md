# EKS Terraform AWS Project DEMO

## 📌 Project Overview
I designed this project to **automate the deployment of an Amazon Elastic Kubernetes Service (EKS) cluster** using **Terraform**. I also deployed an **OpenTelemetry demo application**, leveraging **Docker and Kubernetes** for a scalable, monitored microservices environment.

The project demonstrates **Infrastructure as Code (IaC)**, **containerization**, and **observability** using **OpenTelemetry**.

## 🎯 Objectives
- Automate **EKS cluster deployment** using **Terraform**
- Deploy a **sample OpenTelemetry demo application**
- Implement **containerized services** using **Docker & Kubernetes**
- Enable **monitoring & observability** using OpenTelemetry
- Use **multi-stage Docker builds** for optimized security & efficiency
- Deploy an **Ingress Controller for advanced traffic routing**

## ⚙️ Installation & Setup
### **Prerequisites**
Before running the project, I ensured I had the following installed:

- **Terraform** (>= 1.2.0)
- **AWS CLI** (configured with necessary IAM permissions)
- **kubectl** (for managing Kubernetes resources)
- **Docker** (for building & running containerized applications)
- **Helm** (for package management in Kubernetes)

### **Steps I Followed to Deploy the Infrastructure**
1. **Cloned the repository**
```sh
git clone https://github.com/jomaa-ahmed/Eks-terraform-aws-Project.git
cd Eks-terraform-aws-Project
```
2. **Initialized Terraform**
```sh
terraform init
```
3. **Applied Terraform Configuration**
```sh
terraform apply -auto-approve
```
4. **Retrieved Kubernetes Configuration**
```sh
aws eks --region <your-region> update-kubeconfig --name <cluster-name>
```

## 🚀 Running the Project
Once the EKS cluster was up and running, I accessed the **OpenTelemetry Demo application**:

### **Homepage Preview**
![Homepage](./images/1.png)

The homepage of the OpenTelemetry demo application was accessible at:
```
http://<public-ip>:8080
```

### **Product Page Preview**
![Product Page](./images/2.png)

## 🐳 Docker & Deployment
I containerized the application services using **Docker** and deployed them using **Docker Compose**.

### **Starting All Services**
```sh
docker compose up -d
```

#### **Docker Compose Running Services**
![Docker Compose](./images/3-docker compose up.png)

### **Golang-based Microservice (Product Catalog)**
I built the backend service using **Golang** and implemented a **multi-stage Docker build** for efficiency.

#### **Dockerfile for Golang Service**
![Golang Dockerfile](./images/4-golang-Dockerfile.png)

### **Java-based Microservice (Ad Service)**
I built an **advertisement service** using Java and Gradle with a **multi-stage Docker build**.

#### **Dockerfile for Java Service**
![Java Dockerfile](./images/6-Java-Dockerfile.png)

### **Python-based Microservice (Recommendation Service)**
I built a **recommendation service** using Python.

#### **Dockerfile for Python Service**
![Python Dockerfile](./images/7-python-Dockerfile.png)

### **Re-running Docker Compose**
```sh
docker compose up -d
```

#### **Updated Docker Compose Running Services**
![Docker Compose Update](./images/8-docker-compose-up.png)

## 🌍 Terraform State Management with S3 & DynamoDB
I used **Amazon S3** and **DynamoDB** to store and manage the Terraform state files securely.

### **Terraform S3 Bucket Configuration**
![Terraform S3 Bucket](./images/11-terraform-s3.png)

### **Main Terraform Configuration (`main.tf`)**
![Main Code Terraform](./images/12-maincodetf.png)

### **Initializing Terraform with S3 Backend for EKS**
![Terraform Init with S3](./images/13-terraform-init-using-s3-backend-eks.png)

### **Terraform Plan for Creating EKS**
![Terraform Plan Create EKS](./images/14-terraform-plan-create-eks.png)

### **`kubectl get nodes` Output Before Configuring EKS**
![kubectl Get Nodes Before Config](./images/15-kubcetl-get-nodesbeforeconfig.png)

### **Terraform Deployment Completed**
![Terraform Done](./images/16-terraform-done.png)

### **AWS CLI Version Verification**
![AWS CLI Version](./images/17-awscli.png)

### **`kubectl get nodes` Output After Configuring EKS**
![kubectl Config Updated](./images/18-kubectlworkingconfig.png)

### **Creating Kubernetes Service Account for OpenTelemetry**
![Service Account Creation](./images/19-createsa.png)

### **Checking Kubernetes Services and Pods**
![Check Services & Pods](./images/20-check-svc-and-pods.png)

### **Deploying Ingress Controller & LoadBalancer**
![Helm Repo Add](./images/26-helm-repo-add.png)

![LB Controller Installed](./images/27-lbcontrollerinstalledusinghelm.png)

![Ingress Config](./images/28-configure-ingress.png)

![Ingress Route](./images/29-configure-ingressroute.png)

![Ingress Host Mapping](./images/30-add-tohost-ipaddress.png)

### **Final Hosted Application**
![Hosted App](./images/32-localingress.png)

## 🔥 Key Technologies Used
- **AWS EKS** (Managed Kubernetes Cluster)
- **Terraform** (Infrastructure as Code)
- **Kubernetes** (Container Orchestration)
- **Docker** (Containerization)
- **Helm** (Kubernetes Package Management)
- **AWS Load Balancer** (Traffic Management)

## 📝 Summary
This project demonstrates how I automated **Kubernetes infrastructure provisioning**, **deployed microservices**, and **integrated observability** using best practices. It showcases hands-on experience in **EKS, Terraform, Ingress Controllers, and Observability**, which is highly relevant for **Cloud-Native DevOps roles**.
