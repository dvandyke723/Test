pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                retry(3) {
                    bat 'echo "Testing"'
                }
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
