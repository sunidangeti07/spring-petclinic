pipeline {
    agent { label'sai_1' } 
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcs') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sunidangeti07/spring-petclinic.git'
            }
        }
        stage('build') {
            steps{
                sh 'mvn package'
            }
        }
    }
    post {
        success {
            subject: 'this project jenkins ${JOB_NAME} from ${JOB_URL}',
            body: 'use this id that is ${BUILD_ID}',
            to: 'saidangeti098@gmail.com'
        }
        failure {
           subject: 'this project jenkins ${JOB_NAME} from ${JOB_URL}',
           body: 'use this id that is ${BUILD_ID}',
           to: 'saidangeti098@gmail.com'
    }
}    