pipeline{
   agent any
    tools {
        jdk 'java'
        maven 'Maven3'
    }
    environment{
        VERSION = "${env.BUILD_ID}"
    }
stages{
        stage("Cleanup Workspace"){
                steps {
                cleanWs()
                }
        }

        stage("Checkout from SCM"){
                steps {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/naragoni22/first-service.git']])
                }
        }

        stage("Build Application"){
            steps {
                sh "mvn clean package"
            }

       }
   stage("docker build & docker push"){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerlogin', variable: 'docker_pass')]) {
                             sh '''
                                docker build -t naresh20/springapp:${VERSION} . 
                                docker push  naresh20/springapp:${VERSION}
                                docker rmi naresh20/springapp:${VERSION}
                            '''
                    }
                }
            }
        }

       stage("Test Application"){
           steps {
                 sh "mvn test"
           }
       }

  }
}
