pipeline {
    agent any

    environment {
        WEBAPP_REPO = "https://github.com/nld91/test-webapps.git"
        WEBAPP_BRANCH = "master"
        PROJECT_PATH = "java/hello-world-sb"
    }
    
    tools {
        // Ensure JDK is configured in Jenkins Global Tool Config
        maven 'Maven 3.6.3'
        jdk 'OpenJDK 11'
    }

    stages {
        stage('Checkout WebApp Repo') {
            steps {
                script{
                    dir('webapp') {
                        git branch: "${WEBAPP_BRANCH}", url: "${WEBAPP_REPO}"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                dir("webapp/${PROJECT_PATH}") {
                    sh 'mvn clean package'
                }
                
            }
        }

        stage('Test') {
            steps{
                echo 'Testing...'
                dir("webapp/${PROJECT_PATH}") {
                    sh 'mvn test'
                }
                
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}