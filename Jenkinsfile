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
      
        stage('Deploy') {
          steps {
            sh '''
               mkdir -p /opt/pet
               scp target/*.jar jenkins@10.0.0.10:/opt/pet/
               '''
            sh "ssh jenkins@10.0.0.10 'nohup java -jar /opt/pet/spring-petclinic-1.5.1.jar &'"
          }
        }
       
    }
}
