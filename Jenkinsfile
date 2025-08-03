pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                echo "→ Récupération du code"
                checkout scm
            }
        }

        stage('Validate CF Template') {
            steps {
                echo "→ Validation du template CloudFormation"
                // On installe AWS CLI si besoin
                sh '''
                    if ! command -v aws ; then
                      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
                      unzip awscliv2.zip
                      ./aws/install
                    fi
                '''
                // Validation du template
                sh '''
                    aws cloudformation validate-template \
                      --template-body file://create_ec2_IAM_SG.yaml
                '''
            }
        }

        stage('Test') {
            steps {
                echo "→ Exécution de tests fictifs"
                // par exemple, un simple shell script ou un appel curl
                sh 'echo "Tests unitaires OK !"'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline terminé avec succès'
        }
        failure {
            echo '❌ Échec du pipeline'
        }
    }
}


