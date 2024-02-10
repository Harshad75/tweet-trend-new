def registry = 'https://harshad7777.jfrog.io'
def Image_Name = 'harshad7777.jfrog.io/docker-dops-workshop-docker-local/devops-docker-first'
def Ver_Sion = '2.1.3'




pipeline {
    agent {
	node{
         label 'maven-slave'
	}
    }
    stages {
        stage('Parallel Jobs') {
            parallel {
                stage('Job A') {
                    steps {
                        echo 'Running Job A'
			sh 'cat deploy.sh'
			sh 'systemctl status docker'
			
			sh 'mkdir efgh'
			sh 'rm -rf abcd.txt'
			sh 'touch efgh/abcd.txt'
			    
                        // Add steps for Job A here
                    }
                }
                stage('Job B') {
                    steps {
                        echo 'Running Job B'
                        // Add steps for Job B here
                    }
                }
                stage('Job C') {
                    steps {
                        echo 'Running Job C'
                        // Add steps for Job C here
                    }
                }
            }
        }
    }
}
  
