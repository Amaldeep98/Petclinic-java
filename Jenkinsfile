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
}
