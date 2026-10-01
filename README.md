# Docker Jenkins ECR CI/CD Project

## 📌 Project Overview

This project demonstrates an end-to-end **CI/CD pipeline** for a Python Flask application using **GitHub, Jenkins, Docker, and Amazon Elastic Container Registry (ECR)**.

The pipeline automatically pulls the application source code from GitHub, builds a Docker image, authenticates with AWS ECR, tags the Docker image, and pushes the image to the ECR repository. After a successful deployment pipeline, an AWS Lambda function is invoked as a post-build action.

## 🛠️ Technologies Used

* Python
* Flask
* Docker
* Jenkins
* Jenkins Pipeline
* GitHub
* AWS CLI
* Amazon ECR
* AWS Lambda
* Linux/Shell scripting

## 🏗️ Project Architecture

GitHub Repository
↓
Jenkins Pipeline
↓
Clone Source Code
↓
Docker Image Build
↓
AWS ECR Authentication
↓
Docker Image Tagging
↓
Push Image to Amazon ECR
↓
AWS Lambda Invocation

## 🔄 CI/CD Pipeline Stages

### 1. Clone Code

Jenkins retrieves the application source code from the GitHub repository.

### 2. Build Docker Image

The application is containerized using the Dockerfile and a Docker image is created with a build-specific tag.

### 3. Login to Amazon ECR

Jenkins uses the AWS CLI to authenticate Docker with the Amazon ECR registry.

### 4. Tag Docker Image

The locally built image is tagged with the ECR repository URL and Jenkins build number.

### 5. Push Docker Image

The tagged Docker image is pushed to the Amazon ECR repository.

### 6. Post-Build Action

After a successful pipeline execution, Jenkins invokes an AWS Lambda function.

## 🐳 Docker Configuration

The application uses Python 3.9 as the base image.

The Dockerfile:

* Uses Python 3.9
* Creates `/app` as the working directory
* Copies the application files
* Installs dependencies from `requirements.txt`
* Starts the Flask application

## 🌐 Application

The project contains a simple Flask application that exposes a web endpoint and runs on port `5000`.

The application returns:

`CI/CD Pipeline Working!`

## ⚙️ Jenkins Pipeline

The Jenkinsfile defines the following stages:

* Clone Code
* Build Image
* Login ECR
* Tag Image
* Push Image

The pipeline uses the Jenkins `BUILD_NUMBER` to create unique Docker image tags, helping identify individual builds.

## ☁️ AWS Integration

The project integrates Jenkins with AWS services:

**Amazon ECR**

* Stores the Docker image
* Provides a container registry for the built application

**AWS Lambda**

* Invoked after a successful Jenkins pipeline execution

## 🎯 Key Learning Outcomes

Through this project, I practiced:

* Building CI/CD pipelines using Jenkins
* Containerizing Python applications using Docker
* Creating and tagging Docker images
* Integrating Jenkins with AWS
* Authenticating Docker with Amazon ECR
* Pushing container images to ECR
* Automating post-build AWS operations
* Using Jenkins Pipeline syntax
* Working with GitHub-based source control

## 📂 Project Structure

```text
docker-jenkins-ecr-project/
│
├── Dockerfile
├── Jenkinsfile
├── app.py
└── requirements.txt
```

## 🚀 Workflow

```text
Developer
    ↓
GitHub
    ↓
Jenkins
    ↓
Docker Build
    ↓
Docker Image
    ↓
Amazon ECR
    ↓
AWS Lambda
```

## 🔐 Security Note

AWS credentials and other sensitive information should be stored securely using Jenkins Credentials or AWS IAM mechanisms rather than hard-coded in source files.

## 📌 Project Purpose

The main objective of this project is to demonstrate how a Python application can be automatically **built, containerized, and published to an AWS container registry through a Jenkins CI/CD pipeline**.
