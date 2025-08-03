pipeline {
    agent any

    triggers {
        githubPush() // Déclenche le pipeline automatiquement à chaque push
    }

    environment {
        // Ajoute ici si besoin d'AWS_ACCESS_KEY_ID ou autres secrets
    }

    stages {

        stage('Checkout') {
            steps {
                echo "→ Récupération du code"
                checkout scm
            }
        }

        stage('Install AWS CLI & Validate CF Template') {
            steps {
                echo "→ Validation du template CloudFormation"
                sh '''
                    # Vérifie si AWS CLI est déjà installé
                    if ! command -v aws >/dev/null 2>&1; then
                        echo "AWS CLI non détecté. Installation..."
                        curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
                        rm -rf aws
                        unzip -o awscliv2.zip
                        ./aws/install
                    else
                        echo "AWS CLI déjà installé"
                    fi

                    # Affiche la version pour vérification
                    aws --version

                    # Validation du template YAML
                    aws cloudformation validate-template \
                      --template-body file://create_ec2_IAM_SG.yaml
                '''
            }
        }

        stage('Test') {
            steps {
                echo "→ Exécution de tests fictifs (à remplacer par de vrais tests)"
                sh '''
                    echo "✅ Test fictif réussi"
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline terminé avec succès !"
        }
        failure {
            echo "❌ Échec du pipeline"
        }
    }
}
