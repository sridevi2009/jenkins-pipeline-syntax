pipeline {
    agent {
        node {
          label 'Agent-1'
        }
    }
    environment { 
        GREETING = "HELLO-JENKINS"
    }
    options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()
    }
    // triggers {
    //     cron('H */4 * * 1-5')
    // }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
         stage('code') {
            steps {
                sh """
                 # sleep 10
                """
            }
        }
        stage('Build') {
            steps {
                echo 'This is building..'
            }
        }
        stage('Test') {
            steps {
                echo 'This is testing..'
            }
        }
        stage('Release') {
            steps {
                echo 'Hi im releasing this code for futher process....'
            }
        }
         stage('Deploy') {
            steps {
                sh """
                    echo "here i wrote shell-script"
                    echo "$GREETING" 
                """
            }
        }
         stage('Operate') {
            steps {
                echo 'This is checked by the operation team..'
            }
        }
        stage('Monitoring') {
            steps {
                echo 'This is in the process of Montoring ..'
            }
        }
        stage('plan') {
            steps {
                echo 'FInally at last this code is planning..'
            }
        }
        stage('check params') {
            steps {
                
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
                  
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure {
            echo 'This runs when pipeline is failed, used generally to send some alerts'
        }
        success { 
            echo 'This will run when STAGE is SUCCESS, used generally to send some NOTIFICATIONS'
        }
        aborted { 
            echo 'Usually due to when PIPELINE is MANUALLY ABORTED'
        }
        regression { 
            echo ' This will run when current PIPELINE or STATUS is FAILED'
        }
    }
}