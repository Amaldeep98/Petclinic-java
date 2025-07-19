pipeline {
    agent any 
    
    tools{
        jdk 'jdk17'
        maven 'maven3.9'
    }
    
    stages{
        
        stage("build"){
            steps{
                sh "mvn clean package"
            }
        }
        
         stage("Test Cases"){
            steps{
                sh "mvn test"
            }
        }
        
        stage("Sonarqube Analysis "){
            steps{
                withSonarQubeEnv('Sonarqube') {
                    sh 'mvn sonar:sonar'
    
                }
            }
        }
         
    }
    post {
        success {
            githubNotify context: 'CI', status: 'SUCCESS', description: 'Build passed'
        }
        failure {
            githubNotify context: 'CI', status: 'FAILURE', description: 'Build failed' 
        }
    }
}
