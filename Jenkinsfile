pipeline {
    agent any
    stages {
        stage("Git Checkout") {
           steps{
            script{
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/devopseje/devops_java_app_CICD.git"
                )

            }
        }

        }

    }
}