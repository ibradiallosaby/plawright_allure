pipeline {
    agent {
        docker{
            image 'mcr.microsoft.com/playwright:v1.65.0-jammy'
            args '-u root --entrypoint='
        }
    }

    stages {
         stage('Check version nodejs') {
            steps {
                sh 'npm --version'
            }
        }
        stage('installation dependances') {
            steps {
                sh 'npm install'
                sh 'npm install -D allure-playwright'
            }
        }
        stage('Lancer le test') {
            steps {
                sh "npx playwright test"
                sh 'allure generate allure-results --clean'

            }
        }

         stage('Generer le rapport allure') {
            steps {
                sh 'allure generate allure-results --clean'

            }
        }
         stage('Ouvrir le rapport') {
            steps {
                sh 'allure open'

            }
        }
         
    }
} 

                // script{
                //     if(params.isTags == true){
                //         sh "npx playwright test"
                //     }else {
                //         sh "npx playwright test --grep '${params.TAG}'"
                //     }
                // }