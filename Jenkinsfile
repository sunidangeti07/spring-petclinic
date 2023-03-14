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
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
                            allowEmptyResults: true
                jUnitResultArchiver: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
    post {
        success {
            mail subject: "Jenkins build of ${JOB_NAME} with id ${BUILD_ID} is success",
                body: "use this URL ${BUILD_URL} for more info",
                to: 'saidangeti098@gmail.com'
        }
        failure {
            mail subject: "Jenkins build of ${JOB_NAME} with id ${BUILD_ID} is failure",
                body: "use this URL ${BUILD_URL} for more info",
                to: 'saidangeti098@gmail.com'
        }
    }
}       