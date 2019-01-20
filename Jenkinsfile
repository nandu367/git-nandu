pipeline {
    agent any
    stages{
      stage('stg'){
          steps{
              echo "this works"
          }
      }
       stage('promote'){
           steps{
               timeout(time: 10, unit: 'SECONDS'){
               input 'promote to prod?'
               }
           }
       }
       stage('prd'){
           steps{
               echo "this is working"
           }
       }
            }
    }
nandu
test
