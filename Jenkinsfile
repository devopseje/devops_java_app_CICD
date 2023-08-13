@Library('my-shared-library') _
pipeline {
    agent any
    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/destroy')
    }

    stages {
        
        when { expression { param.action == 'create'}}

        stage("Git Checkout") {
           steps{

                gitCheckout(
                    branch: "main",
                    url: "https://github.com/devopseje/devops_java_app_CICD.git"
                )
               }

        }
        stage("Unit Test Using Maven") {

         when { expression { param.action == 'create'}}    
           steps{

             script{
                mvnTest()
             }
               
            }

        }  

        stage("Unit Integrationstest Using Maven") {
        when { expression { param.action == 'create'}}
           steps{
            
             script{
                mvnIntegrationTest()
             }
               
            }

        } 

        stage("sonarqube ") {
        when { expression { param.action == 'create'}}
           steps{
            
             script{
               staticCodeAnalysis()
             }
               
            }

        }            

    }
}