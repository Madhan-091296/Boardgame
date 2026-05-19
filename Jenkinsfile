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
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
        stage('Build Package') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            echo 'Build completed successfully'
        }
        failure {
            echo 'Build failed'
        }
        always {
            echo 'Pipeline execution completed'
        }
    }
}
