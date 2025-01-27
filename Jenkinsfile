pipeline {
    agent any

    stages {
        
        stage('Fetching Code') {
            steps {
                git 'https://github.com/Arun182901/simple-java-maven-app.git'
            }
        }
        
        stage('Install Maven') {
            steps {
                script {
                    // Check if Maven is already installed
                    def mavenInstalled = sh(script: 'mvn -v', returnStatus: true)
                    if (mavenInstalled != 0) {
                        echo "Maven is not installed. Installing..."
                        sh 'sudo apt update -y && sudo apt install maven -y'
                    } else {
                        echo "Maven is already installed."
                    }
                }
            }
        }

        stage('Build Package') {
            steps {
                echo "Building the package with Maven..."
                sh 'sudo mvn clean package'
            }
        }

    }
}
