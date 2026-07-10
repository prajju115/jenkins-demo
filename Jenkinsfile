pipeline {

    agent any

    options {
        timestamps()
    }

    environment {
        APP_NAME = "Jenkins Maven Demo"
        VERSION = "1.0"
        OWNER = "Prajwal"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/prajju115/jenkins-demo.git'
            }
        }

        stage('Environment') {
            steps {
                echo "Application : ${APP_NAME}"
                echo "Version : ${VERSION}"
                echo "Owner : ${OWNER}"
            }
        }

        stage('Build') {
            steps {
                sh 'cd jenkins-maven-demo && mvn clean package'
            }
        }

    }

    post {

        always {
            echo "Pipeline Finished"
        }

        success {
            echo "Build Successful"
        }

        failure {
            echo "Build Failed"
        }
    }
}
