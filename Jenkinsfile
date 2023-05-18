pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/seunghyejeong/gitops-repository.git']]])
            }
        }
        stage('Build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
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
}
