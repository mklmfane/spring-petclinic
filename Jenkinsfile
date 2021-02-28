
pipeline {
      agent { docker 'maven:3.5-alpine'}
      
      stages {
          stage('Checkout') {
               steps {
                    sh '''  
                       git 'https://github.com/mklmfane/spring-petclinic.git'
                       pwd
                       '''
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
