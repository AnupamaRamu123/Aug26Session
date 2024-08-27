pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'build the war'
            }
        }
        
        stage("Deploy to QA") {
            steps {
                echo 'deploy to QA'
            }
        }
        
        stage('Checkout') {
            steps {
                git url: 'https://github.com/AnupamaRamu123/Aug26Session'
            }
        }
        
        stage('Run api testcases using Newman') {
            steps {
                bat 'newman run ./Aug22CollectionForJenkins3.postman_collection.json -e ./Aug22EnvForJenkins3.postman_environment.json -r cli,htmlextra --reporter-htmlextra-export ./results/Aug26PipeplinePractice.html'           }
        }
        
        stage('Publish HTML Extra Report'){
            steps{
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: false, 
                    keepAll: true, 
                    reportDir: 'results', 
                    reportFiles: 'Aug26PipeplinePractice.html', 
                    reportName: 'Aug26PipelinePracticeHTMLExtraReport', 
                    reportTitles: ''
                ])
            }
        }
        
        stage("Deploy to PROD"){
            steps{
                echo("deploy to PROD")
            }
        }
    }
}
