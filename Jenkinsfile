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
          sh 'mvn -f takeiteasy-macroprocess/pom.xml -Dmaven.test.failure.ignore=true install' 
      }
      post {
        success {
            sh '''
              ls -lah
              pwd
            '''
            junit 'target/surefire-reports/**/*.xml' 
        }
      }
    }
  }
}