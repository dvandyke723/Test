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
            }
        }
        stage('build') {
            steps {
                retry(3) {
                    bat 'echo "Building (Maven)"'
                    bat 'mvn package -f d:/ApacheMaven_3.5.2/bin/my-app/pom.xml'
                }
            }
        }
        stage('binary repository') {
            steps {
                retry(3) {
                    bat 'echo "Adding to Binary Repository (Nexus)"'
                    bat 'mvn clean deploy -f d:/ApacheMaven_3.5.2/bin/my-app/pom.xml'
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
