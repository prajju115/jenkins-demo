pipeline {

    agent any

    options {
        timestamps()
    }

    parameters {

        string(
            name: 'APP_NAME',
            defaultValue: 'Jenkins Maven Demo',
            description: 'Enter Application Name'
        )

        string(
            name: 'VERSION',
            defaultValue: '1.0',
            description: 'Enter Application Version'
        )

        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'UAT', 'PROD'],
            description: 'Select Deployment Environment'
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
                sh 'cd jenkins-maven-demo && mvn clean package'
            }
        }

    }

    post {

        success {
            echo "Build Successful"
        }

        always {
            echo "Pipeline Finished"
        }
    }
}
