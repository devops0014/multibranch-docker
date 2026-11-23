
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }

        stage('Tag') {
            steps {
                sh 'docker tag image1 kedarmahesh/kiddo-mart:bank'
            }
        }

        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push kedarmahesh/kiddo-mart:bank'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d --name bank-app -p 1111:80 kedarmahesh/kiddo-mart:bank'
            }
        }
    }
}
