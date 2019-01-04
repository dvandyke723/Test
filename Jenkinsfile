pipeline {
    agent any
    tools {
        jdk 'JDK'
        maven 'Maven'
    }
    stages {
        stage('code quality') {
            steps {
                retry(3) {
                    bat 'echo "Code Quality Test"'
                    bat 'cd /d "d:/ApacheMaven_3.5.2/bin/my_app"'
                    bat 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=365b9714ed23e75254b6098241bcf6a9c4fb2aee'
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
