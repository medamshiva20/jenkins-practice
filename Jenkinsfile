pipeline {
    agent { node { label 'agent1' } }
    options{
        timeout(time: 1, unit: 'HOURS') 
    }
    environment{
        USER = 'sivamedam'
    }
        parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
        stage('credentails')
        {
            environment {
                AUTH = credentails('ssh-auth')
            }
            steps{
                sh 'printenv'
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