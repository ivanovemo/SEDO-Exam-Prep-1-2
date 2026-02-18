pipeline {
    agent any
    environment {
        DOTNET = '/usr/local/share/dotnet/dotnet'
    }
    stages {
        stage('Restore dependencies') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                sh '"$DOTNET" restore SoftUniBazar.sln'
            }
        }

        stage('Build the app') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                sh '"$DOTNET" build SoftUniBazar.sln --no-restore'
            }
        }

        stage('Run the tests') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                sh '"$DOTNET" test SoftUniBazar.sln --no-build --verbosity normal'
            }
        }
    }
}
