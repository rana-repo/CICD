pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage("Build"){
            steps{
                dir('java-source'){
                    sh 'mvn package'
                }
            }
        }
        stage("code quality check using Sonarqube"){
            steps{
                script{
                        withSonarQubeEnv(credentialsId: 'sonar') {
                            dir('java-source'){
                                sh 'mvn  -U clean install sonar:sonar'
                        }
                    }
                }
            }
        }
    }
}