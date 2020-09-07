node{
  stage('SCM Checkout'){
    git credentialsId: 'My_repo', url: 'https://github.com/prath1234/Sonarqube_test'
  }
 stage("build & SonarQube analysis") {
         sh 'mvn clean package'
      }
}
