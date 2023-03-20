pipeline {
    agent { label 'sai_1' } 
    stages {
        stage('vcs') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sunidangeti07/spring-petclinic.git'
            }
        }
        stage('sonarqube analysis') {
            steps {
                withSonarQubeEnv('sonar_name') {
                      // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.5') {
                        sh 'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=sunidangeti07_jenkins3 -Dsonar.organization=sunidangeti07'
                    }    
                }
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
                    junit testResults: '**/surefire-reports/TEST-*.xml'
            } 
        } 
        stage('push to s3 bucket) {
            steps {
                sh 'aws s3 cp /target/spring-petclinic-3.0.0-SNAPSHOT.jar s3://sai-22'
            }
        } 
        
    }
}  
