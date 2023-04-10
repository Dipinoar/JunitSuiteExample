pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Dipinoar/JunitSuiteExample.git'
                sh 'mvn clean compile'
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
    }
}
