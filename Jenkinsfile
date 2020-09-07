node{
  stage('SCM Checkout'){
    git credentialsId: 'My_repo', url: 'https://github.com/prath1234/Sonarqube_test'
  }
 stage("build & SonarQube analysis") {
         sh 'mvn clean package'
      }
  stage('Sonar Analysis'){
   withSonarQubeEnv('SonarQube') {
       sh "/var/lib/jenkins/apache-maven-3.6.0/bin/mvn clean install  
-Dsonar.host.url=http://sonar.optum.com
-Dsonar.login=6690089c8a82788b6b95e0ddc834e4c7d67b211b "
     }
   timeout(time: 5, unit: 'MINUTES') { 
          def qg = waitForQualityGate() 
          if (qg.status != 'OK') {
            error "Pipeline aborted due to quality gate failure: ${qg.status}"
          }
        }

  }
}
