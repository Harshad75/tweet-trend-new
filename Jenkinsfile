pipeline {
  agent {
    node {
      label 'maven'
    }
  }

environment {
  PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
}

  stages {
    stage("Build the Source Code") {
      steps {
        sh 'mvn clean deploy -Dmaven.test.skip=true'
      }
    }
    stage("Unit Test") {
      steps {
        sh 'mvn surefire-report:report'
      }
    }

    stage('SonarQube analysis') {
      environment {
       scannerHome = tool 'sonar_scanner'
      }
      steps{ 
        withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
        sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
    stage("Quality Gate"){
      steps {
        script {
          timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
          def ng = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
          if (ng.status != 'OK') {
            error "Pipeline aborted due to quality gate failure, Please check the source code and reduce bugs and Code smells: ${ng.status}"
          }
          }    
        }     
      }
    }
  }
}
  
