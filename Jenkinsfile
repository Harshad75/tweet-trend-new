pipeline {
  agent {
    node {
      label 'maven'
    }
  }


  stages {
    stage('Clone the source code by using SCM') {
      steps {
        git branch: 'main', url: 'https://github.com/Harshad75/tweet-trend-new.git' 
      }
    }
  }

}
