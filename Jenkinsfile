pipeline {
    agent any

    environment {
        name = 'chinnmay'
    }

    parameters {
        string(name: 'person', defaultValue: 'Tanmay Kota', description: "Who are you?!")
        booleanParam(name: 'isMale', defaultValue: true, description: "Are you male?")
        choice(name: 'City', choices: ['Jaipur', 'Mumbai', 'Pune'], description: "Select City")
    }

    stages {
        stage('Run a command') {
            steps {
                bat 'echo Hello World'
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
                bat '''
                echo BUILD_ID=%BUILD_ID%
                echo Name=%name%
                echo Username=%username%
                '''
            }
        }

        stage('Parameters') {
            steps {
                bat '''
                echo Deploy on test
                echo Person=%person%
                echo Is Male=%isMale%
                echo City=%City%
                '''
            }
        }

        stage('Continue') {
            input {
                message "Should we continue?"
                ok "Yes, we should"
            }
            steps {
                bat 'echo Deploying on production'
            }
        }
    }

    post {
        always {
            bat 'echo I will say hello again'
        }
        success {
            bat 'echo Success'
        }
        failure {
            bat 'echo Failure'
        }
    }
}
