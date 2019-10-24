pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
        stage('Archive Artifact'){
            steps{
                sh 'npm pack | tail -n 1'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/movie-analyst-ui-*.tgz', fingerprint: true
        }
    }
}