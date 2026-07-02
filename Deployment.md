# 



# Flight Reservation Application
A comprehensive cloud-native flight reservation system built with modern technologies and deployed on AWS infrastructure using Kubernetes orchestration.

## 📋 Table of Contents
- Description
- Architecture
- Technology Stack
- Prerequisites
- Getting Started
    - Installation
    - Configuration
    - Deployment

- Project Structure
- API Reference
- Contributing
- License
---

## 📖 Description
The Flight Reservation Application is a full-stack web application that enables users to search, book, and manage flight reservations. Built with a microservices architecture, the application leverages containerization and Kubernetes for scalable deployment on AWS cloud infrastructure.

### Key Features
- **Flight Search**: Search available flights by origin, destination, and date
- **Reservation Management**: Book, view, and cancel flight reservations
- **User Authentication**: Secure user registration and login functionality
- **Responsive UI**: Modern web interface for seamless user experience
- **Cloud-Native Deployment**: Containerized application deployed on AWS EKS
---

## 🏗️ Architecture
```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              AWS CLOUD                                       │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                         VPC (Virtual Private Cloud)                    │  │
│  │                                                                        │  │
│  │  ┌─────────────────────────────────────────────────────────────────┐  │  │
│  │  │                    Amazon EKS Cluster                            │  │  │
│  │  │                                                                  │  │  │
│  │  │  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐         │  │  │
│  │  │  │   Node 1    │    │   Node 2    │    │   Node 3    │         │  │  │
│  │  │  │             │    │             │    │             │         │  │  │
│  │  │  │ ┌─────────┐ │    │ ┌─────────┐ │    │ ┌─────────┐ │         │  │  │
│  │  │  │ │   Pod   │ │    │ │   Pod   │ │    │ │   Pod   │ │         │  │  │
│  │  │  │ │ (App)   │ │    │ │ (App)   │ │    │ │ (App)   │ │         │  │  │
│  │  │  │ └─────────┘ │    │ └─────────┘ │    │ └─────────┘ │         │  │  │
│  │  │  └─────────────┘    └─────────────┘    └─────────────┘         │  │  │
│  │  │                                                                  │  │  │
│  │  │  ┌────────────────────────────────────────────────────────────┐ │  │  │
│  │  │  │              Kubernetes Services                           │ │  │  │
│  │  │  │  • LoadBalancer Service (External Access)                  │ │  │  │
│  │  │  │  • ClusterIP Service (Internal Communication)              │ │  │  │
│  │  │  └────────────────────────────────────────────────────────────┘ │  │  │
│  │  └─────────────────────────────────────────────────────────────────┘  │  │
│  │                                                                        │  │
│  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐   │  │
│  │  │   Amazon RDS    │    │   Amazon ECR    │    │    Route 53     │   │  │
│  │  │   (Database)    │    │ (Container Reg) │    │      (DNS)      │   │  │
│  │  └─────────────────┘    └─────────────────┘    └─────────────────┘   │  │
│  │                                                                        │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘

                                    │
                                    │ HTTPS
                                    ▼
                            ┌───────────────┐
                            │    Users      │
                            │  (Browsers)   │
                            └───────────────┘
```
### Application Flow Diagram
```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│              │     │              │     │              │     │              │
│    User      │────▶│   Frontend   │────▶│   Backend    │────▶│   Database   │
│   Browser    │     │   (JSP/HTML) │     │ (Spring Boot)│     │   (MySQL)    │
│              │◀────│              │◀────│              │◀────│              │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                            │                    │
                            │                    │
                            ▼                    ▼
                     ┌──────────────┐     ┌──────────────┐
                     │   Static     │     │   REST API   │
                     │   Assets     │     │   Endpoints  │
                     │  (CSS/JS)    │     │              │
                     └──────────────┘     └──────────────┘
```
### CI/CD Pipeline Flow
```
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│         │    │         │    │         │    │         │    │         │
│  Code   │───▶│  Build  │───▶│  Test   │───▶│  Push   │───▶│ Deploy  │
│  Commit │    │  (Maven)│    │         │    │  (ECR)  │    │  (EKS)  │
│         │    │         │    │         │    │         │    │         │
└─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘
     │              │              │              │              │
     │              │              │              │              │
     ▼              ▼              ▼              ▼              ▼
  GitHub        Jenkins/       JUnit         Amazon         kubectl
              GitHub Actions               ECR            apply
```
---

## 🛠️ Technology Stack
### Backend Technologies
| Technology | Version | Description | Installation Link |
| ----- | ----- | ----- | ----- |
| **Java** | 11+ | Programming Language | [Download Java](https://www.oracle.com/java/technologies/downloads/)  |
| **Spring Boot** | 2.7.x | Application Framework | [Spring Boot](https://spring.io/projects/spring-boot)  |
| **Maven** | 3.8+ | Build Tool | [Download Maven](https://maven.apache.org/download.cgi)  |
| **MySQL** | 8.0 | Relational Database | [Download MySQL](https://dev.mysql.com/downloads/mysql/)  |
### Frontend Technologies
| Technology | Description | Installation Link |
| ----- | ----- | ----- |
| **JSP** | Java Server Pages | Included with Spring Boot |
| **HTML5/CSS3** | Markup & Styling | N/A |
| **JavaScript** | Client-side scripting | N/A |
| **Bootstrap** | CSS Framework | [Bootstrap](https://getbootstrap.com/)  |
### DevOps & Cloud Tools
| Technology | Description | Installation Link |
| ----- | ----- | ----- |
| **Docker** | Containerization | [Download Docker](https://docs.docker.com/get-docker/)  |
| **Kubernetes** | Container Orchestration | [Install kubectl](https://kubernetes.io/docs/tasks/tools/)  |
| **AWS CLI** | AWS Command Line Interface | [Install AWS CLI](https://aws.amazon.com/cli/)  |
| **eksctl** | EKS Cluster Management | [Install eksctl](https://eksctl.io/installation/)  |
| **Terraform** | Infrastructure as Code | [Download Terraform](https://www.terraform.io/downloads)  |
| **Git** | Version Control | [Download Git](https://git-scm.com/downloads)  |
---

## ✅ Prerequisites
Before setting up the project, ensure you have the following installed:

- [ ] **Java JDK 11 or higher**
- [ ] **Apache Maven 3.8+**
- [ ] **Docker Desktop**
- [ ] **kubectl CLI**
- [ ] **AWS CLI v2**
- [ ] **eksctl**
- [ ] **Git**
- [ ] **AWS Account with appropriate permissions**
### Verify Installations
```bash
# Check Java version
java -version

# Check Maven version
mvn -version

# Check Docker version
docker --version

# Check kubectl version
kubectl version --client

# Check AWS CLI version
aws --version

# Check eksctl version
eksctl version

# Check Git version
git --version
```
---

## 🚀 Getting Started
### Installation
#### Step 1: Clone the Repository
```bash
# Clone the repository
git clone https://github.com/CloudwithKetan/flight-reservation-app.git

# Navigate to project directory
cd flight-reservation-app
```
#### Step 2: Install Java JDK
**For Ubuntu/Debian:**

```bash
sudo apt update
sudo apt install openjdk-11-jdk -y
```
**For macOS:**

```bash
brew install openjdk@11
```
**For Windows:**

1. Download from [Oracle JDK](https://www.oracle.com/java/technologies/downloads/) 
2. Run the installer
3. Set `JAVA_HOME`  environment variable
#### Step 3: Install Maven
**For Ubuntu/Debian:**

```bash
sudo apt install maven -y
```
**For macOS:**

```bash
brew install maven
```
**For Windows:**

1. Download from [Maven Downloads](https://maven.apache.org/download.cgi) 
2. Extract to desired location
3. Add `bin`  directory to PATH
#### Step 4: Install Docker
**For Ubuntu:**

```bash
# Update package index
sudo apt-get update

# Install prerequisites
sudo apt-get install ca-certificates curl gnupg lsb-release -y

# Add Docker's official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Set up repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y

# Add user to docker group
sudo usermod -aG docker $USER
```
**For macOS/Windows:**
Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/) 

#### Step 5: Install AWS CLI
**For Linux:**

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
**For macOS:**

```bash
brew install awscli
```
**For Windows:**
Download and run the [AWS CLI MSI installer](https://awscli.amazonaws.com/AWSCLIV2.msi) 

#### Step 6: Install kubectl
**For Linux:**

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```
**For macOS:**

```bash
brew install kubectl
```
**For Windows:**

```powershell
choco install kubernetes-cli
```
#### Step 7: Install eksctl
**For Linux:**

```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
```
**For macOS:**

```bash
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl
```
**For Windows:**

```powershell
choco install eksctl
```
---

### Configuration
#### Step 1: Configure AWS CLI
```bash
# Configure AWS credentials
aws configure
```
Enter the following when prompted:

- AWS Access Key ID
- AWS Secret Access Key
- Default region (e.g., `us-east-1` )
- Default output format (e.g., `json` )
#### Step 2: Configure Application Properties
Create or update `src/main/resources/application.properties`:

```properties
# Server Configuration
server.port=8080

# Database Configuration
spring.datasource.url=jdbc:mysql://<RDS_ENDPOINT>:3306/flightreservation
spring.datasource.username=<DB_USERNAME>
spring.datasource.password=<DB_PASSWORD>
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# View Resolver
spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp
```
#### Step 3: Set Environment Variables
```bash
# Export environment variables
export DB_HOST=<your-rds-endpoint>
export DB_NAME=flightreservation
export DB_USERNAME=<your-db-username>
export DB_PASSWORD=<your-db-password>
export AWS_REGION=us-east-1
```
---

### Deployment
#### Step 1: Build the Application
```bash
# Navigate to project directory
cd flight-reservation-app

# Clean and build with Maven
mvn clean package -DskipTests

# Verify the JAR file is created
ls -la target/*.jar
```
#### Step 2: Build Docker Image
```bash
# Build Docker image
docker build -t flight-reservation-app:latest .

# Verify image is created
docker images | grep flight-reservation
```
#### Step 3: Create Amazon ECR Repository
```bash
# Create ECR repository
aws ecr create-repository \
    --repository-name flight-reservation-app \
    --region us-east-1

# Get ECR login password and authenticate Docker
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com
```
#### Step 4: Push Image to ECR
```bash
# Tag the image
docker tag flight-reservation-app:latest <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/flight-reservation-app:latest

# Push to ECR
docker push <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/flight-reservation-app:latest
```
#### Step 5: Create EKS Cluster
```bash
# Create EKS cluster using eksctl
eksctl create cluster \
    --name flight-reservation-cluster \
    --region us-east-1 \
    --nodegroup-name standard-workers \
    --node-type t3.medium \
    --nodes 3 \
    --nodes-min 1 \
    --nodes-max 4 \
    --managed

# Verify cluster is running
kubectl get nodes
```
#### Step 6: Create Kubernetes Deployment
Create `k8s/deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: flight-reservation-app
  labels:
    app: flight-reservation
spec:
  replicas: 3
  selector:
    matchLabels:
      app: flight-reservation
  template:
    metadata:
      labels:
        app: flight-reservation
    spec:
      containers:
      - name: flight-reservation
        image: <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/flight-reservation-app:latest
        ports:
        - containerPort: 8080
        env:
        - name: SPRING_DATASOURCE_URL
          valueFrom:
            secretKeyRef:
              name: db-credentials
              key: url
        - name: SPRING_DATASOURCE_USERNAME
          valueFrom:
            secretKeyRef:
              name: db-credentials
              key: username
        - name: SPRING_DATASOURCE_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-credentials
              key: password
        resources:
          requests:
            memory: "512Mi"
            cpu: "250m"
          limits:
            memory: "1Gi"
            cpu: "500m"
---
apiVersion: v1
kind: Service
metadata:
  name: flight-reservation-service
spec:
  type: LoadBalancer
  selector:
    app: flight-reservation
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
```
#### Step 7: Create Kubernetes Secrets
```bash
# Create secret for database credentials
kubectl create secret generic db-credentials \
    --from-literal=url='jdbc:mysql://<RDS_ENDPOINT>:3306/flightreservation' \
    --from-literal=username='<DB_USERNAME>' \
    --from-literal=password='<DB_PASSWORD>'
```
#### Step 8: Deploy to Kubernetes
```bash
# Apply deployment
kubectl apply -f k8s/deployment.yaml

# Verify deployment
kubectl get deployments
kubectl get pods
kubectl get services

# Get external URL
kubectl get service flight-reservation-service
```
#### Step 9: Verify Deployment
```bash
# Check pod status
kubectl get pods -o wide

# View pod logs
kubectl logs -f <pod-name>

# Describe service to get LoadBalancer URL
kubectl describe service flight-reservation-service
```
---

## 📁 Project Structure
```
flight-reservation-app/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── flightreservation/
│   │   │           ├── FlightReservationApplication.java
│   │   │           ├── controllers/
│   │   │           │   ├── FlightController.java
│   │   │           │   ├── ReservationController.java
│   │   │           │   └── UserController.java
│   │   │           ├── entities/
│   │   │           │   ├── Flight.java
│   │   │           │   ├── Passenger.java
│   │   │           │   ├── Reservation.java
│   │   │           │   └── User.java
│   │   │           ├── repositories/
│   │   │           │   ├── FlightRepository.java
│   │   │           │   ├── ReservationRepository.java
│   │   │           │   └── UserRepository.java
│   │   │           └── services/
│   │   │               ├── FlightService.java
│   │   │               ├── ReservationService.java
│   │   │               └── UserService.java
│   │   ├── resources/
│   │   │   ├── application.properties
│   │   │   └── data.sql
│   │   └── webapp/
│   │       └── WEB-INF/
│   │           └── views/
│   │               ├── findFlights.jsp
│   │               ├── displayFlights.jsp
│   │               ├── completeReservation.jsp
│   │               └── reservationConfirmation.jsp
│   └── test/
│       └── java/
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── configmap.yaml
├── Dockerfile
├── pom.xml
└── README.md
```
---

## 📚 API Reference
### Flight Endpoints
| Method | Endpoint | Description |
| ----- | ----- | ----- |
| `GET`  | `/flights`  | Get all flights |
| `GET`  | `/flights/{id}`  | Get flight by ID |
| `POST`  | `/flights/search`  | Search flights by criteria |
### Reservation Endpoints
| Method | Endpoint | Description |
| ----- | ----- | ----- |
| `GET`  | `/reservations`  | Get all reservations |
| `GET`  | `/reservations/{id}`  | Get reservation by ID |
| `POST`  | `/reservations`  | Create new reservation |
| `DELETE`  | `/reservations/{id}`  | Cancel reservation |
### User Endpoints
| Method | Endpoint | Description |
| ----- | ----- | ----- |
| `POST`  | `/users/register`  | Register new user |
| `POST`  | `/users/login`  | User login |
| `GET`  | `/users/{id}`  | Get user details |
### Sample API Requests
**Search Flights:**

```bash
curl -X POST http://<LOAD_BALANCER_URL>/flights/search \
  -H "Content-Type: application/json" \
  -d '{
    "from": "NYC",
    "to": "LAX",
    "departureDate": "2024-03-15"
  }'
```
**Create Reservation:**

```bash
curl -X POST http://<LOAD_BALANCER_URL>/reservations \
  -H "Content-Type: application/json" \
  -d '{
    "flightId": 1,
    "passengerName": "John Doe",
    "passengerEmail": "john@example.com",
    "passengerPhone": "1234567890"
  }'
```
---
## 🙏 Acknowledgments
- Spring Boot Documentation
- AWS Documentation
- Kubernetes Documentation
- Docker Documentation


