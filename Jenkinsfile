pipeline {
    //agent {docker { image 'maven:3.6.3'}}
  //agent {docker { image 'node:23.6'}}
  agent any
     tools{
     maven 'Apache Maven 3.8.4'
     }

  stages{
  stage('Build Maven')
  steps{
  checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/naragoni22/first-service.git']])}
  sh 'maven clean install'
  }
//       stages {
//         stage('Build') {
//             steps {
//                 echo "Building.."
//                 echo "PATH - $PATH"
//                 echo "BUILD_NUMBER - $env.BUILD_NUMBER"
//                 echo "BUILD_ID - $env.BUILD_ID"
//                 echo "JOB_NAME - $env.JOB_NAME"
//                 echo "BUILD_TAG - $env.BUILD_TAG"
//                 echo "BUILD_URL - $env.BUILD_URL"
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo "Testing.."
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 echo "Deploying...."
//             }
//         }
//          stage('Build docker image') {
//             steps {
//                 script{
//                    dockerImage = docker.build("naresh20/hello-world-java:${env.BUILD_TAG}")
//                 }
//
//             }
//         }
//         stage('push docker image') {
//             steps {
//                 script{
//                    docker.withRegistry('', 'dockerhub'){
//                    dockerImage.push();
//                    dockerImage.push('latest');
//                    }
//                 }
//
//             }
//         }
//     }
}