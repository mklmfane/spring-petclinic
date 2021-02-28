
pipeline {
      agent { docker 'maven:3.5-alpine'}
      
      stages {
          stage('Checkout') {
               steps {
                    git 'https://github.com/mklmfane/spring-petclinic.git'
                     }
          }
        
          stage('Build') {
              steps {
                    sh '''
                       pwd
                       mvn clean package
                    '''
                    junit '**/target/surefire-reports/TEST-*.xml'
                    }
          }
     }  
}
