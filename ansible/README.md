End-to-End Automated Web Application Deployment

Project Overview

A DevOps internship project demonstrating web application deployment using AWS EC2, Git, GitHub, Docker, Apache HTTP Server, Jenkins CI/CD, and Ansible.

Intern

Mujahid Pasha

Technologies

- AWS EC2 and Ubuntu Linux
- Git and GitHub
- Docker and Apache HTTP Server
- Jenkins Pipeline
- Ansible

Architecture

GitHub stores the source code. Jenkins checks out the code, validates project files, builds a Docker image, deploys the container, and verifies the website. Ansible automates server preparation.

Project Files

- "index.html" — Website
- "Dockerfile" — Apache container configuration
- "Jenkinsfile" — CI/CD pipeline
- ".dockerignore" — Docker build exclusions
- "ansible/inventory.ini" — Ansible inventory
- "ansible/setup.yml" — Server configuration playbook

Deployment Commands

Build the image:

sudo docker build -t internship-web:1.0 .

Run the container:

sudo docker run -d --name internship-web --restart unless-stopped -p 80:80 internship-web:1.0

Verify:

sudo docker ps
curl http://localhost

Ansible Verification

ansible-playbook -i ansible/inventory.ini ansible/setup.yml --syntax-check
ansible-playbook -i ansible/inventory.ini ansible/setup.yml --become

Jenkins

Create a Pipeline job named "Internship-Web-CI-CD" and configure it to load the "Jenkinsfile" from the "main" branch.

Troubleshooting

- Check EC2 security group rules for ports 22, 80, and 8080.
- Check Docker using "sudo systemctl status docker".
- Check Jenkins using "sudo systemctl status jenkins".
- Ensure port 80 is free before deploying the container.
- Never commit passwords, private keys, or cloud credentials.

Result

The project aims to automate building, deploying, and verifying a website. Complete deployment and pipeline success must be verified on the EC2 server before claiming a successful live deployment.

Internship Submission

Repository: "devops-internship-deployment"
