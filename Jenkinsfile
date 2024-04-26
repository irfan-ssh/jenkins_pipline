pipeline {
    agent any
    environment{
        name = 'irfan'
    }
    parameters {
        string(name: 'personName', defaultValue: 'irfan sheikh', description: 'Whatt is your name?')
        booleanParam(name: 'Male', defaultValue: true, description: 'Are you male? ')
        choice(name: 'Env', choices: ['test','stage', 'qa', 'prod'], description: 'chosse you Environment')
    }
    stages {
        stage('Run commands on linux server') {
            steps {
                sh '''
                ls
                date
                pwd
                '''
                
            }
        }
        stage('Environment variable') {
            environment{
                username = 'sir irfan'
            }
            steps {
                
                sh 'echo "name from main veriables : ${name}"'
                sh 'echo "username from inside variable : ${username}"'
            }
        }
        stage('Parameters') {
            steps {
                sh 'echo "Your name is : ${personName}"'
                sh 'echo "Are you male : ${Male}"'
                sh 'echo "Your environement name : ${Env}"'
            }
        }
        stage('Continue ?') {
            input {
                message "Should we continue ?"
                ok "yes we should"
            }
            steps {
                echo 'Hello this production server'
                
            }
        }
        stage('Deploy on Prod Server') {
            steps {
                echo 'Hello this production server'
                
            }
        }
    }
    post {
        always {
            echo "this is will execute in every case either full build is faild"
        }
        failure {
            echo "this will only run when build is : fail"
        }
        success {
            echo "this will only run when full Job is :  success"
        }
    }
}