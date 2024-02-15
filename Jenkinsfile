// scripted pipeline
pipeline {
    agent any
    stages {
        stage("checkout") {
            steps{
                git branch: 'main', url: 'https://github.com/g0t4/course3-jenkins-gs-spring-petclinic.git'
            }
        }
        
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
