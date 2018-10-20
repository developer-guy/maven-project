pipeline {
          node {
            stages {
            stage('Build'){
                    sh 'mvn clean package'
                    archiveArtifacts artifacts: '**/target/*.war', onlyIfSuccessful: true
                }
            stage('Deploy to Staging') {
                build 'deploy-to-staging'
            }
          }
        }
      }
