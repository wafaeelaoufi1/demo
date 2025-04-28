pipeline {
    agent any

    tools {
        // Spécifie la version de Maven à utiliser
        maven 'M3' // 'M3' est le nom de l'installation Maven configurée dans Jenkins
    }

    stages {
        // Étape 1: Récupération du code source
        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/votre-utilisateur/votre-repo.git'
            }
        }

        // Étape 2: Nettoyage
        stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }

        // Étape 3: Compilation et tests
        stage('Build & Test') {
            steps {
                sh 'mvn compile test'
            }
            post {
                // Archivage des résultats de test
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        // Étape 4: Création du package
        stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
        }
    }

    post {
        // Actions après l'exécution du pipeline
        success {
            echo 'Pipeline exécuté avec succès!'
        }
        failure {
            echo 'Le pipeline a échoué!'
        }
    }
}