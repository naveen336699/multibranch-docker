pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 naveenb2575/paytm:bank'
            }
        }
       stage('push') {
            steps {
                script{
                withDockerRegistry(credentialsId: 'dockerhub') {
                  sh 'docker push naveenb2575/paytm:bank'
                   }
                }
            }
        }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 naveenb2575/paytm:bank'
            }
        }
    }
}
