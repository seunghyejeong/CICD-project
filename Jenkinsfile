def projects = [
  'edu-msa-board-master',
  'edu-msa-comment-master',
  'edu-msa-file-master',
  'edu-msa-ui-master',
  'edu-msa-user-master'
]

pipeline {
  agent any

  stages {
    stage('Checkout Projects') {
      steps {
        git url: 'https://github.com/seunghyejeong/gitops-repository.git', branch: 'main'
      }
    }

    stage('SonarQube Analysis') {
      steps {
        script {
          for (def project in projects) {
            dir(project) {
              withSonarQubeEnv('sonarqube') {
                sh 'mvn clean package sonar:sonar'
              }
            }
          }
        }
      }
    }
  }
}
