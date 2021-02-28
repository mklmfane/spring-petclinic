
pipeline {
      agent { docker 'maven:3.6-alpine'}
      
      stages {
          stage('Checkout') {
               steps {
                       git 'https://github.com/mklmfane/spring-petclinic.git'
                     }
          }
        
          stage('Build') {
              steps {
                    sh '''
                       cd spring-petclinic
                       mvn clean package
                    '''
                    junit '**/target/surefire-reports/TEST-*.xml'
                    }
          }
     }  
}
