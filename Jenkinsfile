pipeline {
    agent {
        label 'aws-agent'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'docker build -t java-app .'
                }
            }
        }
        stage('Push') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'password', usernameVariable: 'username')]) {
                        // some block
                        sh 'docker login --username $username --password $password'
                        sh 'docker tag java-app $username/java-app'
                        sh 'docker push $username/java-app'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {  // Corrected 'setps' to 'steps'
                script {
                    withAWS(credentials: 'aws-cli', region: 'us-east-2') {
                        // some block
                        sh 'aws eks update-kubeconfig --region us-east-2 --name eks'
                        sh 'kubectl apply -f ./k8s/deployment.yaml'
                    }
                }
            }
        }
    }
}