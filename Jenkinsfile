pipeline {
  agent any
  tools {
    maven 'maven-3' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat10(credentialsId: 'tomcat_credential', path: '', url: 'http://localhost:8010/manager/html')], contextPath: '/pipeline', onFailure: false, war: 'webapp/target/*.war' 
        }
      }
    }
  }
}
