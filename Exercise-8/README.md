# Exercise 8: Jenkins Hello World Job

## Objective
To create and execute a Jenkins Freestyle job that retrieves a shell script from GitHub and runs it.

## Tools Used
- Jenkins LTS
- Docker Desktop
- Git and GitHub
- Visual Studio Code

## GitHub Repository
https://github.com/EshwarMayank/devops-sample-code

## Script: hello-world.sh
```bash
#!/bin/bash
echo "Hello, Jenkins!"
```

## Procedure
1. Created a public GitHub repository named `devops-sample-code`.
2. Created `hello-world.sh` and pushed it to GitHub.
3. Opened Jenkins at `http://localhost:8080`.
4. Created a Freestyle job named `HelloWorld`.
5. Configured Git Source Code Management with the GitHub repository URL and `main` branch.
6. Added the build step `sh hello-world.sh`.
7. Saved the job and clicked **Build Now**.
8. Opened Console Output to verify the result.

## Result
The Jenkins job executed successfully and printed `Hello, Jenkins!`. The console reported `Finished: SUCCESS`.

## Screenshots
Screenshots of repository creation, script creation, Git push, Jenkins configuration, and successful build are included in the `screenshots` folder.