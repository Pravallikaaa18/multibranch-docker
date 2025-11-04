pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 pravallikapasupuleti/paytm:bus'
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
                sh 'docker run -itd --name bus-app -p 2222:80 pravallikapasupuleti/paytm:bus'
            }
        }
    }
}
