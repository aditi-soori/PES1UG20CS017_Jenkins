
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'g++ -o  PES1UG20CS017-1 PES1UG20CS017-1.cpp'
            }
        }
        
        stage('Test') {
            steps {
                 sh './PES1UG20CS017-1'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'echo "Deploying the application"' // add your deploy commands here
                sh 'kubectl apply -f deployment.yaml' // example deploy command
                sh 'kubectl apply -f service.yaml' // example deploy command
                sh 'echo "Deployment completed"'
            }
        }
    }
    
    post {
        always {
            // check for errors and display "pipeline failed" if found
            script {
                def pipelineStatus = currentBuild.currentResult
                if (pipelineStatus == 'FAILURE') {
                    echo 'pipeline failed'
                }
            }
        }
    }
}
