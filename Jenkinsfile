pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 naveenb2575/paytm:movie'
            }
        }
        stage('push') {
            steps {
                script{
                withDockerRegistry(credentialsId: 'dockerhub') {
                  sh 'docker push naveenb2575/paytm:movie'
                  }
               }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 naveenb2575/paytm:movie'
            }
        }
    }
}
