pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
    stages{
        stage('Check directories'){
            steps{
                sh 'ls'
            }
         }
            
        stage('maven build'){
            steps{
                sh 'mvn clean install package'
            }
        }
    }
}