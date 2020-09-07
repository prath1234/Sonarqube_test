node{
  stage('SCM Checkout'){
    git credentialsId: 'My_repo', url: 'https://github.com/prath1234/Sonarqube_test'
  }
 stage("build & SonarQube analysis") {
         sh 'mvn clean package'
      }
  stage('Sonar Analysis'){
   withSonarQubeEnv('SonarQube') {
-Dsonar.host.url=http://3.236.20.218:80
-Dsonar.login=9a3576df4bd7d8d374f3e796c552fcd98393f617
     }
   timeout(time: 5, unit: 'MINUTES') { 
          def qg = waitForQualityGate() 
          if (qg.status != 'OK') {
            error "Pipeline aborted due to quality gate failure: ${qg.status}"
          }
        }
  }
}
