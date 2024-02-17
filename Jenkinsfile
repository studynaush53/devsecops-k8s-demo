pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' ///
            }
        }   
      stage('Unit Test') {
            steps {
              sh "mvn test"
            }
            post{
              always {
                junit 'target/surefire-reports/*.xml'
                jacaco execPattern: 'target/jacaco.exec'
              }
            }
      }      
    }
}