pipeline {
  agent any
  tools {
    maven 'M3'
    jdk 'jdk8'
  }
  stages {
    stage ('Build') {
      steps {
          sh 'mvn -f takeiteasy-macroprocess/pom.xml install' 
      }
      post {
        success {
            junit 'takeiteasy-macroprocess/target/surefire-reports/**/*.xml' 
        }
        failure {
          mail to: 's.eduardoaugusto@gmail.com',
               subject: 'Failed Pipeline TakeITEasy',
               body: 'Something is wrong'
        }
      }
    }
  }
}