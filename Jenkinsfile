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
        }
}
