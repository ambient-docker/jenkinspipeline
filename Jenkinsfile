pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh '/usr/share/maven/bin/mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Test Deploy to staging'){
            steps{
                build job:'Test-Deploy-to-staging'
             }
        }
    }
}