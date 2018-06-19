pipeline {
  agent any
  tools {
    maven 'M3'
    jdk 'jdk10'
  }
  stages {
    stage ('Initialize') {
      steps {
          sh '''
              echo "PATH = ${PATH}"
              echo "M2_HOME = ${M2_HOME}"
          '''
      }
    }
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