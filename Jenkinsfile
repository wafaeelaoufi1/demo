pipeline {
    agent any
    stages {
        stage('Clean') {
            steps {
                sh 'cd my-app;mvn clean'
            }
        }
        stage('Test') {
            steps {
                sh 'cd my-app;mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'cd my-app;mvn package'
            }
        }
    }
}
