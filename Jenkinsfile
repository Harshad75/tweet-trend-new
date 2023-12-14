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
  }

}
