pipeline {
    agent none
    stages {
        stage('Dotnet Build and Test') {
            agent {
                docker { 
                    image 'mcr.microsoft.com/dotnet/sdk:5.0' 
                    args '-u root:root'
                }
            }
            steps {
                sh 'dotnet build'
                sh 'dotnet test'
            }
        } 
        stage('Typescript build and Test') {
            agent {
                docker { image 'node:14-alpine'}
            }
            steps {
                sh 'cd ./DotnetTemplate.Web && npm ci'
                sh 'cd ./DotnetTemplate.Web && npm run build'
                sh 'cd ./DotnetTemplate.Web && npm run lint'
                sh 'cd ./DotnetTemplate.Web && npm t'
            }
        }
    }
}
