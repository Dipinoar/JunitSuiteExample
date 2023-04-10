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
    
    post {
        always {
            junit 'target/surefire-reports/*.xml'
            archiveArtifacts 'target/*.jar'
            publishHTML(target: [
                allowMissing: false,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'target/site',
                reportFiles: 'index.html'
            ])
        }
    }
}
