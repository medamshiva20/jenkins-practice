pipeline {
    agent { node {label 'label1'} }
        stages {
            stage('Build')
            {
                steps{
                     echo "Building"
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
                    error "This job is failed"
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