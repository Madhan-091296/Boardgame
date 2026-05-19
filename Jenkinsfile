pipeline {
    agent any
    tools {
        maven 'Maven_3.8.1'
        jdk 'Jdk_17'
    }
    parameters {
        string(
            name: 'BRANCH_NAME',
            defaultValue: 'master',
            description: 'Enter GitHub branch name to build'
        )
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: "${params.BRANCH_NAME}",
                    url: 'https://github.com/Madhan-091296/Boardgame.git'
            }
        }
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
