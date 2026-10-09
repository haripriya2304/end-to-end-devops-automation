# End-to-End DevOps Automation Project

## Project Overview

This project demonstrates an end-to-end DevOps workflow using Jenkins, Docker, GitHub Container Registry (GHCR), Terraform, and AWS EC2.

Jenkins automates the build workflow, Docker packages the application into a container image, GHCR stores the image, and Terraform manages the AWS infrastructure.

## Technologies Used

- **Git and GitHub** — Version control and source code management
- **Jenkins** — CI/CD pipeline automation
- **Docker** — Containerization
- **GitHub Container Registry (GHCR)** — Docker image registry
- **Terraform** — Infrastructure as Code (IaC)
- **AWS EC2** — Cloud compute infrastructure
- **AWS IAM** — Identity and access management

## Architecture

```text
GitHub Repository
       |
       v
     Jenkins
       |
       v
  Docker Build
       |
       v
GitHub Container Registry (GHCR)
       |
       v
 Docker Image Available to Deploy

Terraform ----------------> AWS Infrastructure
                                |
                                v
                             AWS EC2
                                |
                                v
                         Application Output
```

## Project Workflow

1. Store the project source code in GitHub.
2. Configure Jenkins to run the CI/CD pipeline.
3. Build a Docker image using the Dockerfile.
4. Authenticate to GHCR using a Jenkins credential.
5. Tag and push the Docker image to GHCR.
6. Use Terraform to provision and manage AWS infrastructure.
7. Access the application using the EC2 public IPv4 address and configured port.

## Related Repositories

- **Terraform Infrastructure and Dockerfile:** [Terraform and Dockerfile Repository](https://github.com/haripriya2304/devops-project)

## Docker Image — GHCR

The Docker image was built and pushed to GitHub Container Registry.

- **Registry:** GitHub Container Registry
- **Image:** `ghcr.io/haripriya2304/devops-nginx`
- **Tag:** `latest`

Pull the image:

```bash
docker pull ghcr.io/haripriya2304/devops-nginx:latest
```

Run the image locally:

```bash
docker run -d -p 8080:80 --name devops-nginx ghcr.io/haripriya2304/devops-nginx:latest
```

Open `http://localhost:8080` to access the container locally.

## Application Output

**Application URL:** `http://13.223.99.159:8083/`

> The EC2 instance must be running, the container/application must be active, and the relevant port must be allowed by the security group's inbound rules. If the instance is stopped, the URL will not be accessible. The public IPv4 address may change after stopping and starting an instance.


### Jenkins Pipeline

![Jenkins Pipeline Build](screenshots/jenkins-build.png)

### GitHub Container Registry (GHCR)

![GHCR Package](screenshots/ghcr-photo6.png)

### Application Output

![Application Output](screenshots/project-photo7.png)

## Security Considerations

- Store GitHub tokens and other secrets in Jenkins Credentials.
- Never commit AWS access keys, GitHub tokens, passwords, or `.env` files.
- Do not commit Terraform state files or sensitive variable files.
- Restrict SSH access to trusted IP addresses.
- Allow only the required application ports in AWS security groups.

## Key Learnings

- Automating CI/CD workflows with Jenkins.
- Building and publishing Docker images to GHCR.
- Managing AWS infrastructure using Terraform.
- Working with EC2, IAM, and security groups.
- Integrating DevOps tools into an end-to-end workflow.
- Troubleshooting build, registry authentication, and cloud connectivity issues.

## Author

**Haripriya V.**

Aspiring Software Engineer | Cloud & DevOps Enthusiast

- GitHub: [haripriya2304](https://github.com/haripriya2304)

