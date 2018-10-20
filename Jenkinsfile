pipeline {
    agent any
        stages {
            stage('Build'){
                steps {
                    sh 'mvn clean package'
                    archiveArtifacts artifacts: '**/target/*.war', onlyIfSuccessful: true
                }
            }
            stage('Deploy to Staging') {
              steps {
                build 'deploy-to-staging'
              }
            }
            stage('Deploy to Production'){
              steps{
                timeout(time: 5, unit: 'DAYS') {
                  input 'Approve PRODUCTION Deployment?'
                }
              }
              post{
                success {
                  echo 'Code deployed to Production'
                }
                failure{
                  echo 'Deployment failed'
                }
              }
            }
        }
}
