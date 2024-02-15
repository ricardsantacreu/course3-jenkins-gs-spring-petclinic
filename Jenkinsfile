// scripted pipeline
pipeline {
    agent any
    stages {
        stage("build"){
            steps{
                sh "./mvnw package"
            }
        }
        
        stage("capture") {
            steps{
                archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
                jacoco()
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
            }        
            
        }
        
    }
    post {
        always {
            sh "echo 'Sending an email with the result...'"
        }
    }
}
