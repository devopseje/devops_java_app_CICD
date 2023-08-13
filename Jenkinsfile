@Library('my-shared-library') _
pipeline {
    agent any
    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/destroy')
    }

    stages {
                
        stage("Git Checkout") {
        when { expression { params.action == 'create'}}    
           steps{

                gitCheckout(
                    branch: "main",
                    url: "https://github.com/devopseje/devops_java_app_CICD.git"
                )
               }

        }
        stage("Unit Test Using Maven") {

         when { expression { params.action == 'create'}}    
           steps{

             script{
                mvnTest()
             }
               
            }

        }  

        stage("Unit Integrationstest Using Maven") {
        when { expression { params.action == 'create'}}
           steps{
            
             script{
                mvnIntegrationTest()
             }
               
            }

        } 

        stage("sonarqube ") {
        when { expression { params.action == 'create'}}
           steps{
            
             script{
               def SonarquebeCredential = 'sonar' 
               staticCodeAnalysis(SonarquebeCredential)
             }
               
            }

        }   

        stage("wait for Quality gate ") {
        when { expression { params.action == 'create'}}
           steps{
            timeout(time: 5, unit: 'MINUTES'){
             script{
               def SonarquebeCredential = 'sonar' 
               qualityGateStatus(SonarquebeCredential)
             }
            }
               
            }

        }   

        stage("Build project") {
        when { expression { params.action == 'create'}}
           steps{
            
             script{
              
               mvnBuild()
             }
               
            }

        }                       

    }
}