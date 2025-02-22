# EKS Terraform AWS Project

## 📌 Project Overview
I designed this project to **automate the deployment of an Amazon Elastic Kubernetes Service (EKS) cluster** using **Terraform**. I also deployed an **OpenTelemetry demo application**, leveraging **Docker and Kubernetes** for a scalable, monitored microservices environment.

The project demonstrates **Infrastructure as Code (IaC)**, **containerization**, and **observability** using **OpenTelemetry**.

## 🎯 Objectives
- Automate **EKS cluster deployment** using **Terraform**
- Deploy a **sample OpenTelemetry demo application**
- Implement **containerized services** using **Docker & Kubernetes**
- Enable **monitoring & observability** using OpenTelemetry
- Use **multi-stage Docker builds** for optimized security & efficiency

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
![Homepage](./1.png)

The homepage of the OpenTelemetry demo application was accessible at:
```
http://<public-ip>:8080
```

### **Product Page Preview**
![Product Page](./2.png)

## 🐳 Docker & Deployment
I containerized the application services using **Docker** and deployed them using **Docker Compose**.

### **Starting All Services**
```sh
docker compose up -d
```

#### **Docker Compose Running Services**
![Docker Compose](./3-docker compose up.png)

### **Golang-based Microservice (Product Catalog)**
I built the backend service using **Golang** and implemented a **multi-stage Docker build** for efficiency.

#### **Dockerfile for Golang Service**
```dockerfile
FROM golang:1.22-alpine AS builder
WORKDIR /usr/src/app
COPY . .
RUN go mod download
RUN go build -o /go/bin/product-catalog .

FROM alpine AS release
WORKDIR /usr/src/app
COPY --from=builder /go/bin/product-catalog .
ENTRYPOINT ["./product-catalog"]
```

![Golang Dockerfile](./4-golang-Dockerfile.png)

### **Building & Running the Service**
#### **Building the Image**
```sh
docker build -t kirox2023/product-catalog:v1 .
```

#### **Running the Container**
```sh
docker run -d -p 8080:8080 kirox2023/product-catalog:v1
```

#### **Confirming the Service is Running**
```sh
docker ps
```

![Docker Run Working](./5-docker-run-working.png)
