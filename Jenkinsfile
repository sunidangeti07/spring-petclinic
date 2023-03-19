pipeline {
    agent { label'sai_1' } 
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
        stage('publish') {
            steps{
        archiveArtifacts artifacts: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar
                        onliIfSuccessful: True 
                      TesrResults: '**/surefire-reports/TEST-*.xml'
            } 
        } 
        stage('push to s3 bucket) {
            steps {
                sh 'aws s3 cp /target/spring-petclinic-3.0.0-SNAPSHOT.jar s3://sai-22'
            }
        }            

    }
}  
