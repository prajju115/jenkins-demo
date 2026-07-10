pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/prajju115/jenkins-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'cd jenkins-maven-demo && mvn clean package'
            }
        }

    }
}
