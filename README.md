<img width="981" height="454" alt="Screenshot 2025-07-20 211328" src="https://github.com/user-attachments/assets/701be6bc-1439-469c-83db-b7441d54a625" />CI/CD Pipeline for Static Website Deployment using Jenkins, Docker, and Ansible
📌 Project Overview
This project implements a complete CI/CD pipeline to deploy a static website using Jenkins, Docker, Ansible, and GitHub. The pipeline automatically builds, tests, and deploys the application to a production server hosted on AWS EC2 instances.

📁 Repository Structure
Forked from: https://github.com/hshar/website
Custom repo: https://github.com/rushtoakshay/website

Contains:
index.html
images/ folder

Dockerfile

🔧 Tools & Technologies Used
Jenkins: CI/CD automation server
Docker: Containerization
Ansible: Provisioning Jenkins and other tools

GitHub: Source code versioning
AWS EC2: Hosting Jenkins, test, and production servers
Java: Jenkins runtime

🧱 EC2 Infrastructure Setup
EC2-1: Jenkins Master Node
EC2-2: Docker Test Environment (staging)
EC2-3: Docker Production Server

🔄 Pipeline Workflow
1. Code Fork and Push
Actor forks the original website repo to their own GitHub account.
Webhook is configured to trigger Jenkins on any commit.

2. Job 1 – Build & Push to Test
Triggered when code is pushed to either master or develop branch.
Jenkins job clones the repo and builds a Docker image.
Image is deployed to EC2-2 (Test Environment).
master branch → Port 81
develop branch → Port 82
Jenkins tests the deployment and validates success.

3. Job 2 – Monitor & Duplicate
Jenkins continuously monitors for changes in GitHub repo.
If changes are detected, it duplicates code for testing.

4. Job 3 – Deploy to Production
Triggered post successful test build.
Jenkins deploys the Docker container to EC2-3 on port 80 (Production Server).

🚀 How to Run This Project
Provision EC2 Instances using AWS.
Install Jenkins on EC2-1 using Ansible.
Configure GitHub Webhook to trigger Jenkins Job 1.

Set up Jenkins Jobs for:

Job 1 (Build and Test)
Job 2 (Sync and Duplicate)
Job 3 (Deploy to Production)

Verify successful container deployment on:

Port 81 for master testing
Port 82 for develop testing
Port 80 for production

✅ Success Criteria
Code changes in GitHub automatically trigger Jenkins.
Docker containers are created and tested on staging.
Production deployment is automated post-validation.

📸 Architecture Diagram

<img width="981" height="454" alt="Screenshot 2025-07-20 211328" src="https://github.com/user-attachments/assets/473cd415-db7d-4729-8464-1000f9fc910d" />
