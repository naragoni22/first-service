pipeline {
     agent any
     tools{
     maven 'maven-3.9.9'
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