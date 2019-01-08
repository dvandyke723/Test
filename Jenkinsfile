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
                    bat 'echo "Code Quality Test (SonarQube through Maven)"'
                    bat 'mvn -f d:/ApacheMaven_3.5.2/bin/my-app/pom.xml sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=365b9714ed23e75254b6098241bcf6a9c4fb2aee'
                }
                retry(1) {
                    bat 'echo "Code Quality Test - Accessing Github"'
                    bat 'mvn -f https://github.com/dvandyke723/Test/tree/master/java-web-project/pom.xml sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=365b9714ed23e75254b6098241bcf6a9c4fb2aee'
                }
            }
        }
        stage('build') {
            steps {
                retry(3) {
                    bat 'echo "Building (Maven)"'
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
