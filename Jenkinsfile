pipeline {
    agent any
    tools {
        jdk 'JDK'
        maven 'Maven'
        sonarqube 'SonarQube'
    }
    stages {
        stage('code quality') {
            steps {
                retry(3) {
                    bat 'echo "Code Quality Test"'
                }
            }
        }
        stage('build') {
            steps {
                retry(3) {
                    bat 'echo "Building"'
                    bat 'mvn --version'
                }
            }
        }
        stage('binary repository') {
            steps {
                retry(3) {
                    bat 'echo "Adding to Binary Repository"'
                }
            }
        }
    }
    post {
        success {
            echo 'Success!'
        }
        failure {
            echo 'Failure!'
        }
    }
}
