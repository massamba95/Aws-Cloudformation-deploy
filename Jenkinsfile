pipeline {
    agent any

    triggers {
        githubPush()    // 👈 Indispensable pour le déclenchement automatique
    }

    stages {
        stage('Git Checkout') {
            steps {
                echo "Mis à jour récupération du code depuis GitHub"
                checkout scm
            }
        }

        stage('Test') {
            steps {
                echo "Exécution de tests fictifs"
            }
        }
    }
}

