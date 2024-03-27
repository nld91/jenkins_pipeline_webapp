# CI/CD Jenkins Pipeline for Web Applications

## Overview

This repository contains the infrastructure and pipeline configuration necessary to build, test, and deploy a Java Spring Boot web application. It utilises Jenkins, a powerful automation server, to implement continuous integration and continuous deployment (CI/CD) practices for the web application which is housed in a separate repository. The repository includes a `Jenkinsfile` that defines the pipeline steps and a Docker Compose file (`compose.yml`) to easily set up and run a Jenkins container locally.

## Repository Structure

-   **Jenkinsfile**: This file contains the pipeline configuration for Jenkins to follow. It defines the steps to checkout, build, test, and deploy the web application.
-   **docker**: This directory contains the `compose.yml` file, which is used to start a Jenkins container pre-configured with the necessary settings and volume to persist data.

## Prerequisites

-   **Docker**: You must have Docker installed on your machine to use the Docker Compose file for setting up Jenkins. Download and install Docker from Docker's official website following their recommended installation steps for your operating system.
-   **Git**: The Jenkins pipeline requires Git to checkout the web application code from the GitHub repository.

## Setting Up Jenkins

1.  **Start Jenkins**: Navigate to the `docker` directory and run the following command to start a Jenkins container using Docker Compose:   
    
    ```docker-compose -f compose.yml up -d```
    
	This command starts a Jenkins server accessible at `http://localhost:8080`. The first time you run this command, Docker will download the Jenkins image, which might take some time depending on your internet connection.
    
2.  **Initial Configuration**: After Jenkins has started, open a web browser and go to `http://localhost:8080`. Follow the on-screen instructions to complete the initial setup of Jenkins. This includes entering the initial admin password, which you can find in the Jenkins container logs or by running the following command in the terminal where you're running your Jenkins container:

	`docker-compose exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword`
    
3.  **Configure Pipeline**: Once Jenkins is set up, you'll need to create a new pipeline job and point it to this repository. The pipeline will use the `Jenkinsfile` for its configuration.
    

## Pipeline Steps

-   **Checkout WebApp Repo**: The pipeline checks out the web application source code from the specified GitHub repository and branch.
-   **Build**: Executes the build process for the web application using Gradle.
-   **Test**: Runs the test suite for the web application, also utilising Gradle.
-   **Deploy**: Placeholder for the deployment steps. This stage should be customised to deploy the built application to your target environment.

## Web Application Repository

The web application is hosted in a separate GitHub repository at the following URL: [https://github.com/nld91/ci-cd-test-webapp-java-springboot.git](https://github.com/nld91/ci-cd-test-webapp-java-springboot.git)

This repository should contain the Java Spring Boot application, including the `gradlew` wrapper for building and testing the application.

You can modify the Jenkinsfile to suit your own web application by simply modifying the `WEBAPP_REPO` environment variable.