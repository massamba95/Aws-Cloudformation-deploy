pipeline {
    agent any

    environment {
        IMAGE_NAME = "mon-image-docker"
        CONTAINER_NAME = "mon-conteneur-jenkins"
        TAG = "latest"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "→ Récupération du code"
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "→ Build de l'image Docker"
                sh "docker build -t ${IMAGE_NAME}:${TAG} ."
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "→ Lancement du conteneur Docker"
                sh "docker run -d --name ${CONTAINER_NAME} ${IMAGE_NAME}:${TAG}"
            }
        }

        stage('Test in Container') {
            steps {
                echo "→ Test dans le conteneur"
                sh "docker exec ${CONTAINER_NAME} echo 'Conteneur fonctionne !'"
            }
        }

        stage('Cleanup') {
            steps {
                echo "→ Nettoyage"
                sh "docker stop ${CONTAINER_NAME} || true"
                sh "docker rm ${CONTAINER_NAME} || true"
            }
        }
    }

    post {
        always {
            echo "→ Nettoyage final"
            sh "docker stop ${CONTAINER_NAME} || true"
            sh "docker rm ${CONTAINER_NAME} || true"
        }
    }
}
