pipeline {
    agent any
        stages {
          node {
            stage('Build'){
                steps {
                    sh 'mvn clean package'
                    archiveArtifacts artifacts: '**/target/*.war', onlyIfSuccessful: true
                }
            }
            stage('Deploy to Staging') {
                build 'deploy-to-staging'  
            }
        }
      }
}
