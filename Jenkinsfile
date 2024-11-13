// declaritve pipline
// pipeline{
//     agent{
//         label 'aws-agent'
//     }
//     stages{
//         stage('build'){
//             steps{
//                 script{
//                     sh 'docker build -t java-app .'
//                 }
//             }
//         }

//         stage('push'){
//             steps{
//                 script{
//                     withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'Password', usernameVariable: 'Username')]) {
//                     sh 'docker login --username $Username --password $Password'
//                     sh 'docker tag java-app $Username/java-app'
//                     sh 'docker push $Username/java-app'
//                     }
//                 }
//             }
//         }

//         stage('deploy'){
//             steps{
//                 script{
//                     withAWS(credentials: 'aws-cli', region: 'us-east-2') {
//                     sh 'aws eks update-kubeconfig --region us-east-2 --name eks'
//                     sh 'kubectl apply -f ./k8s/deployment.yaml'
//                     }
//                 }
//             }
//         }
//     }
// }
// scripted pipline:
// node{
//     git branch: 'main', url: 'https://github.com/DinaGamalMahmoud/simple-java-app.git'

//     stage('build'){
//         try{
//         sh'echo "build Stage"'
//         }
//         catch(Exception e){
//             sh'echo "exception found"'
//             throw e
//         }
//     }
//     stage('test'){
//         if (env.BRANCH_NAME== "feat"){
//             sh'echo "test Stage"'
//         }
//     }
// }
// successfull test 
// declaritive pipline
pipeline {
    agent any 

    stages {
        stage('build') {
            steps {
                script {
                    echo "build in progress"
                }
            }
        }
        stage('test') {
            steps {
                script {
                    echo "test in progress"
                }
            }
        }
    }
}