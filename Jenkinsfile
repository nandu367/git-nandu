
pipeline {
    agent any
    stages{
        stage('para'){
            parallel {
                stage('dev'){
                    steps{
                        echo 'this is working'
                    }
                }
                stage('QA'){
                    steps{
                        echo 'this works'
                    }
                }
            }
        }
    }
}
