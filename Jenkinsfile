pipeline {
    agent { node { label 'agent1' } }
    options{
        timeout(time: 1, unit: 'HOURS') 
    }
    environment{
        USER = 'sivamedam'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                ls -ltrh
                pwd
                echo 'This is for GitHub hook for push event'
                printenv
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                //error 'This is failed'
            }
        }
    }
    post { 
        always { 
            echo 'I will always run wether job is success or not'
        }
        success{
            echo 'I will run only when job is success'
        }
        failure{
            echo 'I will run when job failure'
        }
    }
}