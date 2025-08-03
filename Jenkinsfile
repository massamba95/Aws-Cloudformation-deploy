pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                echo "Récupération du code depuis GitHub"
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
