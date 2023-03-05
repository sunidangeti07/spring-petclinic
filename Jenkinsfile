pipeline{
    agent {label 'sai_1'}
     triggers {
        pollSCM('* * * * *')
        stages{
            stage('vcs'){
                steps{
                    git branch: 'main',
                    url: 'https://github.com/sunidangeti07/spring-petclinic.git'
                }
            }
            stage('build'){
                steps{
                    sh 'mvn package'
                }
            }
        }
    }      
    
}