pipeline {
    agent { label 'linuxcentos' }
    stages {
        stage ('Checkout') {
          steps {
            git 'https://github.com/mklmfane/spring-petclinic.git'
          }
        }
        stage('Build') {
            agent { docker 'maven:3.6-alpine' }
            steps {
                sh '''
                   mvn clean install
                   mvn clean package
                '''
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
