pipeline{
   agent any
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
                    git branch: 'main', credentialsId: 'github', url: 'https://github.com/naragoni22/register-app.git'
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
                                docker login -u naresh20 -p $docker_pass  
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
