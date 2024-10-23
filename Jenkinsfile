pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dhubaccess')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t ignacyuz/flaskapp:latest .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push ignacyuz/flaskapp:latest'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
