pipeline {
    agent any

    environment {
        name = 'chinnmay'
    }

    parameters {
        string(myname: 'person', defaultValue: 'Tanmay Kota', description: "Who are you?!")
        booleanParam(name: 'isMale', defaultValue: true, description: "")
        choice(cityname: 'City', choices: ['Jaipur', 'Mumbai', 'Pune'], description: "Select City")
    }

    stages {
        stage('Run a command') {
            steps {
                echo 'Hello World'
            }
        }

        stage('System Info') {
            steps {
                bat '''
                dir
                date /T
                time /T
                whoami
                '''
            }
        }

        stage('Environment Variables') {
            environment {
                username = 'chinmaykota'
            }
            steps {
                bat 'echo "%BUILD_ID%"'
                bat 'echo "%name%"'
                bat 'echo "%username%"'
            }
        }

        stage('Parameters') {
            steps {
                echo 'Deploy on test'
                bat 'echo "%cityname%"'
                bat 'echo "%myname%"'
            }
        }

        stage('Continue') {
            input {
                message "Should we continue?"
                ok "Yes, we should"
            }
            steps {
                echo 'Deploying on production'
            }
        }
    }

    post {
        always {
            echo 'I will say hello again'
        }
        success {
            echo 'Success'
        }
        failure {
            echo 'Failure'
        }
    }
}
