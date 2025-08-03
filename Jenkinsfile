pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                echo "Nouveau test déclenché automatiquement !"
                checkout scm
            }
        }

        stage('Test') {
            steps {
                echo "Test fictif en cours..."
            }
        }
    }
}
