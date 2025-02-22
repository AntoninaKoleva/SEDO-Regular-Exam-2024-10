pipeline {
    agent any
   
    stages {
        
        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/bin/**', fingerprint: true
        }
        failure {
            echo 'Build or tests failed. Check logs for details.'
        }
    }
}
