pipeline {
    //agent {docker { image 'maven:3.6.3'}}
  agent {docker { image 'node:23.6'}}
    stages {
        stage('Build') {
            steps {
                sh 'node --version'
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}