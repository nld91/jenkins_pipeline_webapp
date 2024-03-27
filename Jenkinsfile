pipeline {
    agent any

    environment {
        WEBAPP_REPO = "https://github.com/nld91/ci-cd-test-webapp-java-springboot.git"
        WEBAPP_BRANCH = "master"
        PROJECT_PATH = "ci-cd-test-webapp-java-springboot"
    }

    stages {
        stage('Checkout WebApp Repo') {
            steps {
                script{
                    git branch: "${WEBAPP_BRANCH}", url: "${WEBAPP_REPO}"
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                    sh './gradlew build'                
            }
        }

        stage('Test') {
            steps{
                echo 'Testing...'
                    sh './gradlew test'                
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}