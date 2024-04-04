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
                }
            }
        }
}