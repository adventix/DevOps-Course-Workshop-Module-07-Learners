pipeline {
    agent none
        stage{
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
