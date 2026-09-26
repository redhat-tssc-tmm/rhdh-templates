# Secured Parasol Insurance Development Environment

This template creates an isolated development environment for working on the Parasol Insurance application with integrated ACS security scanning.

## What gets created

- A feature branch on your Parasol Insurance (Secured) source repository
- A GitOps repository with deployment manifests and CI/CD pipeline configuration
- An ArgoCD Application to deploy and manage your development environment
- A catalog entry in Developer Hub to track your work

## CI/CD Pipeline

When you push code to your feature branch, the pipeline automatically:

1. **Clones** your source code
2. **Builds** with Maven
3. **Runs SonarQube SAST** for code quality analysis
4. **Builds and pushes** a container image to the registry
5. **Scans the image with ACS** (roxctl image scan) for known vulnerabilities
6. **Checks the image against ACS policies** (roxctl image check) for policy violations
7. **Re-rolls out** the application with the updated image
