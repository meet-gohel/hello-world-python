pipeline {
    agent any

    environment {
        // Define any environment variables here
        MAVEN_HOME = tool name: 'Maven-3.6.3', type: 'maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Pull the code from GitHub repository
                git branch: 'main', url: 'https://github.com/meet-gohel/hello-world-python'
            }
        }

        stage('Build') {
            steps {
                // Compile and build the project using Maven
                sh "${MAVEN_HOME}/bin/mvn clean compile"
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                sh "${MAVEN_HOME}/bin/mvn test"
            }
        }

        stage('Package') {
            steps {
                // Package the application (jar, war, etc.)
                sh "${MAVEN_HOME}/bin/mvn package"
            }
        }
    }

    post {
        success {
            echo 'Build and tests were successful.'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}

