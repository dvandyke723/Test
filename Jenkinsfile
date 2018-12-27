pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                retry(3) {
                    bat 'echo "Building"'
                }
            }
        }
        stage('code quality') {
            steps {
                retry(3) {
                    bat 'echo "Code Quality Test"'
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
