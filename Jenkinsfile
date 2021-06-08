pipeline {
    agent any

    stages {
        stage('.NET Operations') {
            environment {
                DOTNET_CLI_HOME  = '/tmp/dotnet_cli_home'
            }   
            agent {
                docker {
                    image 'mcr.microsoft.com/dotnet/sdk:5.0'
                }
            }
            stages {
                stage ('.NET Build') {
                    steps {
                        sh 'dotnet build'
                    }
                }

                stage ('.NET Test') {
                    steps {
                        sh 'dotnet test'
                    }
                }
            }
        }
            

        stage('npm Operations') {  
            agent {
                docker {
                    image 'node:14-alpine'
                }
            }
            stages {
                stage('npm Install') {  
                    steps {
                        dir('DotnetTemplate.Web') {
                            sh 'npm install'
                        }
                    }  
                }
                stage('TypeScript Build') {  
                    steps {
                        dir('DotnetTemplate.Web') {
                            sh 'npm run build'
                        }
                    }  
                }
            }
        } 
    }
}