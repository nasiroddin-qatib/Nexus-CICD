# 🚀 End-to-End CI/CD DevOps Pipeline (GitHub, Jenkins, Maven, SonarQube, Nexus, Ansible & Tomcat)

---

# 📌 Project Overview

This project demonstrates a **complete End-to-End CI/CD DevOps pipeline** using **GitHub, Jenkins, Maven, SonarQube, Nexus Repository, Ansible, and Apache Tomcat**.

Whenever a developer pushes code to the GitHub repository, a **GitHub Webhook automatically triggers the Jenkins pipeline**.

The pipeline performs the following tasks:

* Jenkins automatically pulls the latest source code from GitHub
* Maven builds the application and runs automated tests
* SonarQube performs static code analysis
* Quality Gate verifies code quality
* Maven packages the application into a WAR artifact
* Artifact is uploaded to Nexus Repository
* Ansible deploys the application to multiple Apache Tomcat servers

This setup simulates a **real-world CI/CD pipeline used in DevOps environments**.

---

# 🧭 CI/CD Pipeline Architecture

The following diagram represents the CI/CD pipeline implemented in this project.

```
Developer Push Code
        │
        ▼
GitHub Repository
        │
        ▼
GitHub Webhook Trigger
        │
        ▼
Jenkins Pipeline
        │
        ├── Checkout Code
        ├── Build (Maven)
        ├── Run Tests
        ├── SonarQube Code Analysis
        │
        ▼
Quality Gate Check
        │
        ├── ❌ Failed → Pipeline Stops
        │
        └── ✅ Passed → Continue Pipeline
                        │
                        ▼
                 Package Artifact (WAR)
                        │
                        ▼
              Upload Artifact to Nexus
                        │
                        ▼
              Trigger Ansible Playbook
                        │
                        ▼
            Deploy Application to Tomcat
```

---

# ⚙️ Tech Stack

* Java
* Maven
* Jenkins
* SonarQube
* Nexus Repository Manager
* Ansible
* Apache Tomcat
* Git
* GitHub
* GitHub Webhooks
* AWS EC2
* Linux

---

# 📂 Project Structure

```
End-to-End-CICD-DevOps-Pipeline
│
├── Jenkinsfile
├── pom.xml
├── settings.xml
├── deploy.yml
├── context.xml
├── README.md
│
├── Screenshots
│   ├── EC2-Servers.png
│   ├── Jenkins-Build-History.png
│   ├── SonarQube-CodeQuality-Check.png
│   ├── QualityGate-Passed.png
│   ├── Nexus-Artifacts.png
│   └── Application-Deployment-Success.png
│
└── src
    └── main
        └── webapp
```

---

# ⚙️ Jenkins Pipeline Stages

## 1️⃣ Checkout

Jenkins pulls the latest source code from the GitHub repository.

```
git clone repository-url
```

---

## 2️⃣ Build

```
mvn compile
```

Maven compiles the application source code.

---

## 3️⃣ Test

```
mvn test
```

Runs automated unit tests to verify application functionality.

---

## 4️⃣ SonarQube Code Analysis

```
mvn sonar:sonar
```

SonarQube analyzes the source code and detects:

* Bugs
* Vulnerabilities
* Code Smells
* Security issues

---

## 5️⃣ Quality Gate Validation

After analysis, SonarQube sends the result to Jenkins using a **SonarQube Webhook**.

Jenkins waits for the Quality Gate result.

* If the Quality Gate **fails**, the pipeline stops
* If the Quality Gate **passes**, the pipeline continues

---

## 6️⃣ Package Application

```
mvn package
```

This command generates the final application artifact:

```
target/myapp.war
```

---

## 7️⃣ Upload Artifact to Nexus Repository

The pipeline uploads the generated artifact to **Nexus Repository Manager**.

```
mvn deploy
```

The artifact is stored and versioned in Nexus so it can be used later for deployments.

---

## 8️⃣ Deploy Application using Ansible

Jenkins triggers an **Ansible playbook** which deploys the WAR file to remote Tomcat servers.

```
ansible-playbook deploy.yml
```

Ansible connects to the Tomcat servers using SSH and copies the WAR file into the Tomcat webapps directory.

---

# 📸 Project Screenshots

## AWS EC2 Infrastructure

![EC2 Servers](https://github.com/nasiroddin-qatib/End-to-End-CICD-DevOps-Pipeline/blob/master/Screenshots/EC2-Servers.png)

---

## Jenkins Pipeline Build History

![Jenkins Build History](https://github.com/nasiroddin-qatib/End-to-End-CICD-DevOps-Pipeline/blob/master/Screenshots/Jenkins-Build-History.png)

---

## SonarQube Code Quality Analysis

![SonarQube Code Quality](https://github.com/nasiroddin-qatib/End-to-End-CICD-DevOps-Pipeline/blob/master/Screenshots/SonarQube-CodeQuality-Check.png)

---

## Quality Gate Passed

![Quality Gate Passed](https://github.com/nasiroddin-qatib/End-to-End-CICD-DevOps-Pipeline/blob/master/Screenshots/QualityGate-Passed.png)

---

## Nexus Artifact Repository

![Nexus Artifact](https://github.com/nasiroddin-qatib/End-to-End-CICD-DevOps-Pipeline/blob/master/Screenshots/Nexus-Artifacts.png)

---

## Application Deployment Success

![Application Deployment](https://github.com/nasiroddin-qatib/End-to-End-CICD-DevOps-Pipeline/blob/master/Screenshots/Application-Deployment-Success.png)

---

# 🎯 What This Project Demonstrates

This project demonstrates hands-on experience with:

* Jenkins CI/CD pipeline creation
* GitHub Webhook automation
* Maven build lifecycle
* SonarQube code quality analysis
* Quality Gate validation
* Artifact storage using Nexus Repository
* Automated deployment using Ansible
* Multi-server deployment using Apache Tomcat

---

# 👨‍💻 Author

Developed as part of hands-on practice to strengthen **AWS, DevOps, CI/CD pipelines, artifact management, and automation skills**.
