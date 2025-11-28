# DevOps Internship Assignment: MEAN Stack Deployment

This repository features a full-stack MEAN (MongoDB, Express, Angular, Node.js) application that has been containerized with Docker, orchestrated with Docker Compose and deployed to AWS EC2 instance using a CI/CD pipeline via GitHub Actions.


- **Webpage URL:** http://35.172.164.14/
- **GitHub Repository:** https://github.com/VamsiP19/crud-dd-task-mean-app

---

## Tech Stack Used
* **Containerization:** Docker & Docker Compose
* **CI/CD:** GitHub Actions
* **Cloud Infrastructure:** AWS EC2 (Ubuntu)

### Architecture Overview
The application uses a **Microservices-style** architecture deployed on a single EC2 instance:
1.  **Nginx Container:** Listening on Port 80. Routes `/` to the Angular app and `/api` to the Backend.
2.  **dd-frontend:** The Angular application (built via multi-stage Docker build).
3.  **dd-backend:** The Node.js API server listening on Port 8080.
4.  **mongodb:** Database storage.

---

## Project Screenshots

### 1. Live Application (AWS)
*The deployed application running on the AWS cloud infrastructure.*
<img width="1440" height="900" alt="web_page1" src="https://github.com/user-attachments/assets/48866be9-d398-4fc6-bb9f-e3e5c18e1234" />

<img width="1440" height="900" alt="web_page2" src="https://github.com/user-attachments/assets/7f79af05-62d0-4502-8d19-ac69ded5533a" />

### 2. CI/CD Pipeline Success
*GitHub Actions workflow demonstrating automated Build, Push, and Deploy steps.*
<img width="1440" height="900" alt="gh_action" src="https://github.com/user-attachments/assets/44dbef48-f27e-4387-9833-eda7a3d1f50d" />

### 3. Docker Hub Registry
*Custom images (`dd-frontend` and `dd-backend`) successfully pushed to the registry.*
<img width="1440" height="900" alt="docker_hub" src="https://github.com/user-attachments/assets/9ea83852-2a47-45b9-bdae-e3e0b7ca233f" />

### 4. AWS Infrastructure & Nginx
*Proof of EC2 instance running Ubuntu and Nginx configuration routing.*
<img width="1165" height="48" alt="ec2_info" src="https://github.com/user-attachments/assets/65989750-f521-41cb-87b3-71b70a329144" />

---

## ⚙️ CI/CD Pipeline Details
The project utilizes a **GitHub Actions** workflow (`cicd.yml`) to automate the deployment process:

1.  **Trigger:** Pushes to the `main` branch.
2.  **Docker Build:** Builds optimized images for Frontend and Backend.
3.  **Push:** Pushes images to Docker Hub with tags `dd-frontend` and `dd-backend`.
4.  **Deploy:**
    * Connects to the AWS EC2 instance via SSH.
    * Pulls the latest code and Docker images.
    * Executes `docker-compose up -d` to perform a zero-downtime update.

---

## ☁️ Infrastructure Details
The application is hosted on **Amazon Web Services (AWS)**.

* **Service:** EC2 (Elastic Compute Cloud)
* **Region:** US East (N. Virginia)
* **Instance Type:** t3.micro
* **OS:** Ubuntu 24.04 LTS
* **Security:** Port 80 (HTTP) and Port 22 (SSH) allowed.

---

## 📝 Local Setup Instructions
To run this application locally without AWS:

1.  **Clone the repository:**
    ```bash
    git clone [YOUR_REPO_URL]
    cd crud-dd-task-mean-app
    ```

2.  **Run with Docker Compose:**
    ```bash
    docker-compose up --build
    ```

3.  **Access the App:**
    Open your browser and navigate to `http://localhost`.

---
