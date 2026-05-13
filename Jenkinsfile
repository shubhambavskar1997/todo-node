// pipeline {
//     agent { label 'node-agent' }
    
//     stages{
//         stage('Code'){
//             steps{
//                 git url: 'https://github.com/LondheShubham153/node-todo-cicd.git', branch: 'master' 
//             }
//         }
//         stage('Build and Test'){
//             steps{
//                 sh 'docker build . -t trainwithshubham/node-todo-test:latest'
//             }
//         }
//         stage('Push'){
//             steps{
//                 withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
//         	     sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
//                  sh 'docker push trainwithshubham/node-todo-test:latest'
//                 }
//             }
//         }
//         stage('Deploy'){
//             steps{
//                 sh "docker-compose down && docker-compose up -d"
//             }
//         }
//     }
// }
pipeline {
    agent any

    environment {
        IMAGE_NAME = 'todo-node'
        IMAGE_TAG  = "${BUILD_NUMBER}"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                sh "docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${IMAGE_NAME}:latest"
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
    }
}
