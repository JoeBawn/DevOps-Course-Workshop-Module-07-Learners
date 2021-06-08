pipeline {
    agent any

    stages {
        stage('.NET Build') {
            environment {
                DOTNET_CLI_HOME  = '/tmp/dotnet_cli_home'
            }   
            agent {
                docker {
                    image 'mcr.microsoft.com/dotnet/sdk:5.0'
                }
            }
            steps {
                sh 'dotnet build'
            }
        }

        stage('.NET Test') {
            environment {
                DOTNET_CLI_HOME  = '/tmp/dotnet_cli_home'
            }   
            agent {
                docker {
                    image 'mcr.microsoft.com/dotnet/sdk:5.0'
                }
            }
            steps {
                sh 'dotnet test'
            }
        }

        stage('TypeScript Build') {  
            agent {
                docker {
                    image 'node:14-alpine'
                }
            }
            steps {
                dir('DotnetTemplate.Web') {
                    sh 'npm run build'
                }
                
            }
        }
    }
}