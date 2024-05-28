pipeline {
    agent any
    environment {
        dockerImageFrontend = ''
        dockerImageApi = ''
    }
    stages {
        stage ('Build frontend') {
            steps {
                dir('frontend'){
                    script {
                        dockerImageFrontend = docker.build("detalikota/time-app-frontend-dev", "-f frontend/Dockerfile .")
                    }
                }

            }
        }
        stage('Build api'){
            steps {
                dir('api'){
                    script {
                        dockerImageApi = docker.build("detalikota/time-app-api-dev", "-f api/Dockerfile .")
                    }
                }

            }
        }
        stage ('Push images') {
            steps {
                script {
                    dockerImageFrontend.push()
                    dockerImageApi.push()
                }

            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}