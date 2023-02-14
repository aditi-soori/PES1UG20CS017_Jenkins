
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
                sh 'mvn deploy'
                echo "Deployment successful"  
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
