pipeline {
    agent { node {label 'label1'} }
    options {
     timeout(time: 1, unit: 'HOURS')
    }
    environment {
        USER = 'siva'
    }
        stages {
            stage('Build')
            {
                steps{
                     echo "Building"
                  sh'''
                    ls -ltrh
                    pwd
                    echo "Adding webhook concept in github"
                  '''
                }
            }
            stage('Test'){
                steps{
                     echo "Testing"
                }
            }
            stage('Deploy'){
                steps{
                    echo "Deploy"
                    error "This is error"
                    
                }
            }
            stage('Env') {
            environment { 
                AUTH = credentials('ssh-auth')
            }
            steps {
                sh 'printenv'
            }
        }
        }
        post {
            always {
                echo "I will run the jon always whether it is success or failure"
            }
            success {
                echo "I will run the job if it is only success"
            }
            failure {
                echo "I will send the status if the job only fails"
            }
        }
}