
pipeline {
      agent { docker 'maven:3.6.3-alpine'}
      
      stages {
          stage('Checkout') {
               steps {
                       git 'https://github.com/mklmfane/spring-petclinic.git'
                       sh 'pwd'
                       
                     }
          }
        
          stage('Build') {
              steps {
                    sh 'mvn clean package'
                    junit '**/target/surefire-reports/TEST-*.xml'
                    }
          }
     }  
}
