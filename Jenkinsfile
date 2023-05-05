pipeline {
    agent any

    stages {
        stage('Munit Test') {
            steps {
                echo 'Testing..'
                bat 'mvn clean test'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                bat 'mvn clean install'
            }
        }
        stage('Deploy') {
          environment {

            ANYPOINT_CREDENTIALS = credentials('anypoint.credential')

            }
            steps {
                echo 'Deploying to cloudHub...'
                bat 'mvn clean deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Denv=Sandbox -Dappname=whitelist-api -DvCore=Micro -Dworkers=1'
                echo 'Deployed...'
            }
        }
    }
}
