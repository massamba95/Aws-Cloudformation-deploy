pipeline {
    agent any

    triggers {
        githubPush()    // 👈 Indispensable pour le déclenchement automatique
    }

    stages {
        stage('Git Checkout') {
            steps {
                echo "Mis à jour récupération"
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

