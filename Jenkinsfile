pipeline {
    agent any

    parameters {
        string(name: 'APP_NAME', defaultValue: 'Jenkins Maven Demo')
        string(name: 'VERSION', defaultValue: '1.0')
        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'UAT', 'PROD'],
            description: 'Select Environment'
        )
    }

    stages {

        stage('Display Parameters') {
            steps {
                echo "Application : ${params.APP_NAME}"
                echo "Version : ${params.VERSION}"
                echo "Environment : ${params.ENVIRONMENT}"
            }
        }

        stage('Build') {
            steps {
                sh '''
                cd jenkins-maven-demo
                mvn clean package
                '''
            }
        }

        stage('Deploy') {

            when {
                expression {
                    params.ENVIRONMENT == 'PROD'
                }
            }

            steps {
                echo "Deploying application to Production..."
            }
        }

    }

    post {
        success {
            echo "Pipeline Finished Successfully"
        }
    }
}
