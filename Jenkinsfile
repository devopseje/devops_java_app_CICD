@Library('my-shared-library') _
pipeline {
    agent any
    stages {
        stage("Git Checkout") {
           steps{

                gitCheckout(
                    branch: "main",
                    url: "https://github.com/devopseje/devops_java_app_CICD.git"
                )
               }

        }
        stage("Unit Test Using Maven") {

           steps{
             script{
                mvnTest()
             }
               
            }

        }    

    }
}