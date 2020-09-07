node{
  stage('SCM Checkout'){
    git credentialsId: 'My_repo', url: 'https://github.com/prath1234/Sonarqube_test'
  }
 stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('My SonarQube Server') {
                sh 'mvn clean package sonar:sonar'
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
  }
}
}
