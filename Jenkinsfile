pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        
        stage('Generate Reports') {
            steps {
                sh 'mvn surefire-report:report'
                sh 'mvn jxr:jxr'
            }
        }
    }
}
