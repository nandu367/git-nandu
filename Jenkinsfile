
pipeline {
    agent any
    stages{
        stage('para'){
            parallel {
                stage('dev'){
                    steps{
                        echo 'Working'
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
