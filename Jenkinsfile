pipeline {
    agent { node {label 'label1'} }
    options {
     timeout(time: 1, unit: 'HOURS')
    }
    // triggers{
    //     cron('* * * * *')
    // }
    environment {
        USER = 'siva'
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
                    printenv
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
                    //error "This is error"
                    
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
        stage('params') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
         stage('Input') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
        stage('Prod Deploy')
        {
            when {
                branch 'main'
            }
            steps{
                echo "Deploying to Prod"
            }
        }
    }
        post {
            always {
                echo "I will run the job always whether it is success or failure"
            }
            success {
                echo "I will run the job if it is only success"
            }
            failure {
                echo "I will send the status if the job only fails"
            }
        }
}