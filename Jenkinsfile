pipeline {
    agent { node { label 'agent1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'ls -ltrh'
                sh 'pwd'
                sh 'touch /tmp/file1'
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