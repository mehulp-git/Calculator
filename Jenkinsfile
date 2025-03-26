pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/mehulp-git/Calculator.git'  // GitHub Repository URL
        GIT_BRANCH = 'main'  // Branch name (can be changed based on your requirement)
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the GitHub repository
                git branch: "${env.GIT_BRANCH}", url: "${env.GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                script {
                    // Build the project with Maven (ensure you have Maven installed)
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                // Run unit tests (using Maven's test goal)
                script {
                    // Run Maven test
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploying the artifact (for example, if it's a WAR file, deploying it to Tomcat or another server)
                script {
                    // Example: Deploy to Tomcat or another server (adjust based on your setup)
                    // You may need to change this to match your deployment method.
                    sh 'mvn deploy'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment were successful!'
        }
        failure {
            echo 'There was an issue with the build or deployment.'
        }
    }
}
