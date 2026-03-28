# 🚀 Student Feedback System - DevOps CI/CD Pipeline

## 📌 Project Overview
This project demonstrates the implementation of a **DevOps CI/CD pipeline** to automate the build and deployment of a Student Feedback System web application.

The pipeline integrates version control, continuous integration, containerization, and deployment using **Jenkins, Docker, and AWS EC2**.

---

## 🧰 Tech Stack

- 🐍 Python (Flask)
- 🔧 Jenkins (CI/CD)
- 🐳 Docker (Containerization)
- ☁️ AWS EC2 (Deployment)
- 🔗 Git & GitHub (Version Control)

---

## 🏗️ Architecture
- Developer → GitHub → Jenkins → Docker → EC2 → Live Application
---

## ⚙️ Features

- Automated build and deployment using Jenkins
- Dockerized application for consistency
- Real-time deployment on AWS EC2
- Error handling for container restart
- Scalable and reusable pipeline

---

## 📁 Project Structure
**student-feedback-system/
│
├── app/ # Flask application
├── templates/ # HTML files
├── static/ # CSS, JS files
├── ansible/ # Deployment scripts (optional)
├── Dockerfile # Container configuration
├── Jenkinsfile # CI/CD pipeline**

---

## 🚀 Setup Instructions

### 🔹 1. Clone Repository
git clone https://github.com/vishalkoripala/student-feedback-system.git

cd student-feedback-system

---

### 🔹 2. Run with Docker (Manual)
docker build -t student-feedback-app .
docker run -d -p 5000:5000 student-feedback-app


---

### 🔹 3. Access Application


http://<your-server-ip>:5000
docker build -t student-feedback-app .
docker run -d -p 5000:5000 student-feedback-app


---

### 🔹 3. Access Application


http://56.228.11.11:5000

---

## ⚙️ Jenkins Pipeline

The pipeline automates:

1. Clone code from GitHub  
2. Build Docker image  
3. Run container  

### 📄 Jenkinsfile
pipeline {
agent any
stages {
    stage('Clone Code') {
        steps {
            git 'https://github.com/vishalkoripala/student-feedback-system.git'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t student-feedback-app .'
        }
    }

    stage('Run Container') {
        steps {
            sh 'docker stop student-app || true'
            sh 'docker rm student-app || true'
            sh 'docker run -d -p 5000:5000 --name student-app student-feedback-app'
        }
    }
}
}

---

## 🐳 Docker Configuration


FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r app/requirements.txt
EXPOSE 5000
CMD ["python", "app/app.py"]

---

## ⚠️ Challenges Faced

- Jenkins GPG key error during installation  
- Git branch mismatch (master vs main)  
- OS command mismatch (Windows vs Linux)  
- Docker permission issues  

---

## ✅ Solutions

- Added proper Jenkins repository key  
- Updated branch to `main`  
- Replaced `bat` with `sh` in Jenkinsfile  
- Configured Docker permissions  

---

## 📊 Results

- CI/CD pipeline successfully implemented  
- Automated deployment achieved  
- Application running live on AWS  

---

## 🚀 Future Enhancements

- Add GitHub Webhooks (auto trigger pipeline)
- Push Docker image to Docker Hub
- Use Kubernetes for orchestration
- Add monitoring (Prometheus, Grafana)

---

## 👨‍💻 Author

**Vishal Koripala**

---

## ⭐ Acknowledgment

This project demonstrates real-world DevOps practices including CI/CD automation, containerization, and cloud deployment.
