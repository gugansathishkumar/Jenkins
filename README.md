# 🐳 Jenkins + Docker Integration

This project integrates **Jenkins** with **Docker** to enable Jenkins pipelines to execute Docker commands directly on the AWS EC2 instance.

---

## 📌 Why Integrate Jenkins with Docker?

By default, the Jenkins user does not have permission to interact with the Docker daemon. To allow Jenkins pipelines to build Docker images and manage containers, the Jenkins user must be added to the Docker group.

---

## ⚙️ Integration Steps

### Step 1: Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
```

Verify Docker installation:

```bash
docker --version
```

---

### Step 2: Start and Enable Docker

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

Check Docker status:

```bash
sudo systemctl status docker
```

---

### Step 3: Add Jenkins User to Docker Group

Grant Docker permissions to the Jenkins user.

```bash
sudo usermod -aG docker jenkins
```

---

### Step 4: Restart Services

```bash
sudo systemctl restart docker
sudo systemctl restart jenkins
```

---

### Step 5: Verify Docker Access

Run the following command to ensure the Jenkins user can access Docker.

```bash
sudo -u jenkins docker ps
```

If no permission errors are displayed, the integration has been completed successfully.

---

# 🚀 Jenkins Pipeline

The following pipeline verifies the Docker installation.

```groovy
pipeline {
    agent any

    stages {

        stage('Docker Version') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Running Containers') {
            steps {
                sh 'docker ps'
            }
        }

    }
}
```

---

# ✅ Expected Output

```
Docker version 28.x.x

CONTAINER ID   IMAGE   STATUS   PORTS
```

This confirms that Jenkins is successfully connected to Docker and can execute Docker commands.

---

# 📚 Learning Outcomes

Through this integration, I learned:

- Installing Docker on Ubuntu
- Configuring Jenkins with Docker
- Managing Linux user permissions
- Running Docker commands from Jenkins pipelines
- Automating tasks using Jenkins Pipeline
- Understanding the foundation of CI/CD workflows
