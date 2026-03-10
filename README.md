🚀 Docker to AWS Deployment
ECS + ECR Real-World Project

This project demonstrates how to containerize a Node.js application using Docker and deploy it on AWS using Amazon ECS and Amazon ECR.

The workflow includes:

Launching an EC2 instance

Cloning a Node.js application

Building a Docker image

Pushing the image to Amazon ECR

Deploying the container using Amazon ECS (Fargate)

Monitoring logs using CloudWatch

📌 Architecture

Local Machine → EC2 → Docker Build → Amazon ECR → Amazon ECS (Fargate) → Application Deployment

⚙️ Step 1: Create an EC2 Instance

Go to AWS Console

Navigate to EC2 → Launch Instance

Configure:

OS: Ubuntu

Instance Type: t2.micro

Key Pair: Create or select an existing key pair

Click Launch Instance

💻 Step 2: Connect to EC2 Instance

Connect to your instance using SSH from your local machine.

ssh -i your-key.pem ubuntu@your-ec2-public-ip
🔄 Step 3: Update the System

Update the system packages.

sudo apt update
sudo apt upgrade -y
📂 Step 4: Clone the Project Repository

Clone the Node.js application repository.

git clone https://github.com/LondheShubham153/node-todo-cicd.git
🧹 Step 5: Remove Unnecessary Directories

Remove the following directories from the project:

DevSecOps

terraform

azure-pipelines.yml

kustomize

📦 Step 6: Create Amazon ECR Repository

Go to AWS Console

Navigate to Amazon ECR

Select Create Repository

Configure:

Repository type: Public

Repository name: todo-app

OS: Linux

Click Create Repository

📜 Step 7: Get Push Commands

Open the created repository

Click View Push Commands

Copy the commands for authentication and image push

🔐 Step 8: Create IAM User

Go to IAM → Users

Click Create User

Assign permissions:

AmazonECRFullAccess

AmazonECSFullAccess

Go to Security Credentials

Create Access Keys

🐳 Step 9: Install Docker & AWS CLI

Install Docker on EC2:

sudo apt install docker.io -y

Add user to Docker group:

sudo usermod -aG docker ubuntu

Reboot the instance:

sudo reboot

Install AWS CLI:

sudo apt install awscli -y

Configure AWS credentials:

aws configure

Paste the Access Key and Secret Key created in IAM.

🔑 Step 10: Authenticate Docker to Amazon ECR

Follow the authentication command shown in ECR View Push Commands.

🏗 Step 11: Build and Push Docker Image

Go to project directory:

cd node-todo-cicd

Build Docker image:

docker build -t node-app .

Tag the image:

docker tag node-app:latest public.ecr.aws/g2l2u7w2/node-app:latest

Push image to ECR:

docker push public.ecr.aws/g2l2u7w2/node-app:latest

Verify in ECR → Images that the image is uploaded.

☁️ Step 12: Deploy Using ECS (Fargate)

Go to Amazon ECS

Click Create Cluster

Select Fargate

Enable CloudWatch Container Insights

Create the cluster

Then:

Go to Task Definitions

Create a new task definition

Select Fargate

Deploy and run the task

🌐 Step 13: Access the Application

Go to ECS → Tasks

Click the running task

Copy the Public IP

Open in browser:

http://PUBLIC-IP:8000

⚠️ Ensure Port 8000 is open in the Security Group

📊 Monitoring Logs

Application logs can be monitored using Amazon CloudWatch Logs.

🛠 Technologies Used

Docker

AWS EC2

AWS ECR

AWS ECS (Fargate)

AWS IAM

AWS CloudWatch

Node.js

If you want, I can also make this README much more attractive by adding:

🔥 DevOps tool badges

🐳 Docker & AWS icons

📊 GitHub stats

👀 Visitor counter

🎬 Animated header

Just tell me and I’ll create a professional GitHub README template for you. 🚀
      
      
