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

        stage('Compile Code') {
            steps {
                sh 'mvn clean package'
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
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
