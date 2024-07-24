pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven-3.9.0' 
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/02Poonam/Jenkins_pipeline.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
                }
            }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
