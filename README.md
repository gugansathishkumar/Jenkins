# 🚀 Jenkins + Docker CI/CD Setup on AWS EC2

A hands-on DevOps project demonstrating how to set up **Jenkins** with **Docker** on an **AWS EC2 Ubuntu** instance and create a basic CI/CD pipeline using a **Jenkinsfile**.

---

## 📌 Project Overview

This project showcases the installation and configuration of Jenkins and Docker on an AWS EC2 instance. It also demonstrates how to configure Jenkins to communicate with Docker and execute a simple pipeline successfully.

The goal of this project is to gain practical experience with Continuous Integration (CI), Docker integration, and Jenkins pipeline automation.

---

## 🛠️ Technologies Used

- AWS EC2
- Ubuntu Linux
- Jenkins
- Docker
- Git & GitHub
- Jenkins Pipeline (Pipeline as Code)

---

## ⚙️ Project Architecture

```text
GitHub Repository
        │
        ▼
     Jenkins
        │
        ▼
 Execute Pipeline
        │
        ▼
Docker Engine on EC2
        │
        ▼
 Build & Execute Tasks
```

---

## 📂 Project Workflow

### 1️⃣ Launch AWS EC2 Instance

- Created an Ubuntu EC2 instance
- Configured the Security Group
- Connected using SSH

### 2️⃣ Install Java

Installed Java, which is required to run Jenkins.

```bash
sudo apt update
sudo apt install openjdk-21-jdk -y
java -version
```

---

### 3️⃣ Install Jenkins

- Added the Jenkins repository
- Installed Jenkins
- Started and enabled the Jenkins service

```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
```

---

### 4️⃣ Install Docker

Installed Docker Engine and verified the installation.

```bash
sudo apt install docker.io -y
docker --version
```

---

### 5️⃣ Configure Docker Permissions

Allowed the Jenkins user to access Docker without requiring root privileges.

```bash
sudo usermod -aG docker jenkins
sudo systemctl restart docker
sudo systemctl restart jenkins
```

Verify Docker access:

```bash
sudo -u jenkins docker ps
```

---

### 6️⃣ Configure Jenkins

- Accessed Jenkins through the browser
- Installed recommended plugins
- Created the administrator account
- Configured Jenkins successfully

---

### 7️⃣ Create a Pipeline Job

Created a Pipeline project and added the following Jenkinsfile.

```groovy
pipeline {
    agent any

    stages {

        stage('Hello') {
            steps {
                echo 'Hello, Jenkins!'
            }
        }

        stage('System Information') {
            steps {
                sh 'hostname'
                sh 'pwd'
                sh 'whoami'
                sh 'java -version'
            }
        }

        stage('Complete') {
            steps {
                echo 'Pipeline executed successfully!'
            }
        }
    }
}
```

---

## ✅ Pipeline Result

The pipeline completed successfully and displayed:

- Hostname
- Current Workspace
- Logged-in User
- Java Version
- Successful Build Status

---

## 📷 Project Screenshots

Include screenshots of:

- Jenkins Dashboard
- AWS EC2 Instance
- Docker Installation
- Docker Permission Configuration
- Jenkins Pipeline Configuration
- Successful Pipeline Execution
- Console Output

---

## 📚 Key Learning Outcomes

Through this project, I gained hands-on experience with:

- Jenkins Installation & Configuration
- Docker Installation
- Jenkins-Docker Integration
- Linux User & Group Management
- CI/CD Pipeline Creation
- Jenkinsfile Syntax
- Pipeline as Code
- AWS EC2 Administration
- DevOps Best Practices

---

## 🚀 Future Improvements

- Build Docker Images automatically
- Push Images to Docker Hub
- Integrate GitHub Webhooks
- Deploy Applications using Docker
- Add SonarQube for Code Quality
- Integrate Maven Builds
- Automate Deployments with Ansible
- Extend the pipeline to Kubernetes

---

## 👨‍💻 Author

**Gugan Sathish Kumar**

🎓 Aspiring DevOps Engineer

🔗 GitHub: https://github.com/gugansathishkumar

🔗 LinkedIn: https://www.linkedin.com/in/gugansathishkumar

---

⭐ If you found this project useful, consider giving the repository a **Star**.
