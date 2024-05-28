pipeline {
    agent any
    environment {
        dockerImageFrontend = ''
        dockerImageApi = ''
    }
    stages {
        stage ('Build images'){
            parallel {
                stage ('Build frontend') {
                    steps {
                        script {
                            dockerImageFrontend = docker.build("detalikota/time-app-frontend-dev", "-f frontend/Dockerfile .")
                        }
                    }
                }
                stage('Build api'){
                    steps {
                        script {
                            dockerImageApi = docker.build("detalikota/time-app-api-dev", "-f api/Dockerfile .")
                        }
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