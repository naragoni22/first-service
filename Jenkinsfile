pipeline {
     agent any
     tools{
     maven 'LocalMaven'
     }
     stages{
         stage('Build Maven'){
             steps{
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/naragoni22/first-service.git']])
               sh 'maven clean install'

             }
         }

     }
 }