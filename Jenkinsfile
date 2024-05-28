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
                        dockerImageFrontend = docker.build("detalikota/time-app-frontend-dev", "-f Dockerfile .")
                    }
                }

            }
        }
        stage('Build api'){
            steps {
                dir('api'){
                    script {
                        dockerImageApi = docker.build("detalikota/time-app-api-dev", "-f Dockerfile .")
                    }
                }

            }
        }
        stage ('Push images') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-creds') {
                        dockerImageFrontend.push()
                        dockerImageApi.push()
                    }

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