
pipeline {
   
    agent any
   
    stages{
        stage('checkout-->clone'){
            steps{
                git branch: 'feature-2026.02.19', url: 'https://github.com/github-siva/Pet_clinic-.1.git'
            }
        }
       
        stage('Build'){
            steps{
            bat 'mvn install'
        }
        }
        stage('Test'){
            steps{
                bat 'mvn test'
            }
        }
stage('published the test results'){
            steps{
               junit 'target/*surefire-reports/*.xml'
            }
        }
       
        stage('Generated the Artifacts'){
            steps{
                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }

         stage('deploy'){
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat_credentials', path: '', url: 'http://localhost:8080/')], contextPath: 'tomcat_integrating- pet_clinic.1_pipeline', war: 'target/*.war'
            }
        }
    }
}
 
