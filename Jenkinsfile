pipeline {
    agent any
     
    tools {
        maven 'Maven_3.8.1'
        jdk 'Jdk_17'
    }

    stages {
        
        stage('Compile') {
            steps {
             sh 'mvn compile'
            }
        }
        
        stage('Test') {
            steps {
              sh 'mvn test' 
            }
        }
        
        stage('Build') {
            steps {
              sh "mvn package"
            }
        }
    }
}
