pipeline {
    agent any

    stages {
        stage ('Make an image'){
            parallel {
                stage ('Testing1') {
                    steps {
                        echo "test1"
                    }
                }
                stage('Testing2'){
                    steps {
                        echo "test2"
                    }
                }
            }
        } 
    }
}