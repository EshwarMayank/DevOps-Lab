# Exercise 7: Jenkins CI Automation

## Objective
To install Jenkins using Docker and configure the Jenkins dashboard for Continuous Integration (CI).

## Tools Used
- Docker Desktop
- Jenkins LTS
- Windows PowerShell

## Steps Performed
1. Pulled the Jenkins LTS Docker image.
2. Created and started the Jenkins container.
3. Exposed port 8080 for the Jenkins web interface.
4. Exposed port 50000 for Jenkins agent communication.
5. Retrieved the initial administrator password.
6. Opened Jenkins at `http://localhost:8080`.
7. Completed the initial setup and installed suggested plugins.

## Docker Command

```powershell
docker run -d --name jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
```

## Retrieve Initial Administrator Password

```powershell
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

## Screenshots
Screenshots of the Docker container, Jenkins setup, plugin installation, and dashboard are included in the `screenshots` folder.

## Result
Jenkins was installed and configured using Docker for CI automation.