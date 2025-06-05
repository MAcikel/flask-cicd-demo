Project README — CI/CD Pipeline with GitHub Actions and AWS EC2 Deployment
Overview

This project is a simple Flask web application containerized with Docker and deployed automatically to an AWS EC2 instance via a GitHub Actions CI/CD pipeline.

The pipeline is triggered on every push to the main branch, and it performs the following steps:

Checkout the latest code from the repository.

Log in to Docker Hub using secured credentials stored in GitHub Secrets.

Build the Docker image for the Flask app.

Push the Docker image to Docker Hub.

Connect to the AWS EC2 instance via SSH.

Pull the latest Docker image from Docker Hub on the EC2 instance.

Stop and remove any existing container instance.

Run the updated Docker container, exposing port 80 for web access.

Prerequisites
An AWS EC2 instance with Docker installed and accessible via SSH.

Docker Hub account with repository created.

GitHub repository configured with the following Secrets:

DOCKER_USERNAME — Your Docker Hub username.

DOCKER_PASSWORD — Your Docker Hub password or access token.

EC2_SSH_KEY — The private SSH key (in PEM format) with access to the EC2 instance.

EC2_USER — The SSH username for the EC2 instance (e.g., ec2-user).

Usage
Push your code changes to the main branch.

GitHub Actions will automatically trigger the build-and-deploy workflow.

After successful execution, the new version of the app will be running on your EC2 public IP.

You can access your Flask app using the EC2 public IP in a browser:
http://<YOUR_EC2_PUBLIC_IP>/

Workflow File Location
The CI/CD pipeline is defined in:
.github/workflows/build-and-deploy.yml

Notes and Improvements
The current deployment uses a simple restart strategy by stopping and removing the old container.

For zero-downtime deployment, consider Blue/Green or Canary deployment strategies.

In the future, Kubernetes orchestration can be integrated for scalability and management.

Ensure your EC2 security groups allow inbound traffic on port 80.

Contact
For any questions or feedback, please contact:
Mehmet Acikel – [mehmetacikel@gmail.com]


