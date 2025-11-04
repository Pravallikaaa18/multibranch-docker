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
                sh 'docker tag image1 pravallikapasupuleti/paytm:bank'
            }
        }
        stage('Push') {
            steps {
                script {
                   withDockerRegistry(credentialsId: 'dockerhubpass') {
                        sh 'docker push pravallikapasupuleti/paytm:bank'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 pravallikapasupuleti/paytm:bank'
            }
        }
    }
}
