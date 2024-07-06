## CI/CD Pipeline with Jenkins, Docker, Ansible, and GitHub

![alt text](<project architecture.jpg>)


### Overview

This project implements a CI/CD pipeline to automate building, testing, and deploying a Dockerized application using Jenkins, Docker, Ansible, and GitHub.

### Architecture

- **Developer Workstation**: Code is written and committed to a GitHub repository.
- **GitHub**: Central code repository with webhooks to trigger Jenkins builds.
- **Jenkins Server (GCP VM Instance)**:
  - Auto-pulls latest code from GitHub.
  - Builds Docker image, runs tests, and uses Ansible for deployment.
  - Ansible and latest pip installed for Docker modules.
  - Connected to Docker server via SSH.
- **Docker Server (GCP VM Instance)**: 
  - Builds and deploys Docker containers.
  - Managed and configured using Ansible playbooks.

### Ansible Playbook

The `docker-playbook.yaml` performs tasks such as:

- Synchronizing files from Jenkins to Docker server.
- Stopping and removing existing Docker containers and images.
- Building and starting new Docker containers.

### Workflow

1. **Code Commit**: Developers push changes to GitHub.
2. **Trigger Build**: GitHub webhook notifies Jenkins.
3. **Jenkins Build**: Jenkins pulls code, builds Docker image, and runs tests.
4. **Docker Image Creation**: New Docker image is created and stored.
5. **Deployment**: Ansible deploys the Docker container to the target environment.

### Implementation

- **Servers**: Two GCP VM instances, one for Jenkins and one for Docker.
- **Jenkins Job**: Freestyle job to run Ansible playbook from Git.
- **SSH**: Servers connected via SSH with credentials set in Jenkins job.
- **Demonstration**: CSS site used for demo.

### Benefits

- **Automation**: Reduces manual intervention and errors.
- **Consistency**: Docker ensures consistent environments.
- **Scalability**: Easily scalable architecture.
- **Speed**: Accelerates development lifecycle.

### Tools and Technologies

- **GitHub**: Version control.
- **Jenkins**: Continuous integration.
- **Docker**: Containerization.
- **Ansible**: Configuration management.
- **GCP**: Google Cloud Platform for hosting servers.

---

This CI/CD pipeline ensures efficient and reliable software delivery, enhancing overall development productivity.

