pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                script {
                    // Login to Docker Hub (replace with your credentials or Jenkins creds)
                    bat 'docker login -u siddharthpg -p fghjkl123321Q'

                    // Build and push Docker image
                    bat 'docker build -t w9-dd-app:latest .'
                    bat 'docker tag w9-dd-app:latest siddharthpg/w9-dh-app:latest'
                    bat 'docker push siddharthpg/w9-dh-app:latest'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    bat 'minikube start'
                    bat 'kubectl apply -f my-kube1-deployment.yaml'
                    bat 'kubectl apply -f my-kube1-service.yaml'
                    echo '✅ Deployed successfully to Minikube!'
                }
            }
        }
    }
}
