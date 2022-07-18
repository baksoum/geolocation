pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
    stages{
        stage('maven build'){
            steps{
                sh 'mvn clean install package'
            }
        }
        stage('check pwd'){
            steps{
                sh 'pwd'
            }
        }
        stage('list directory'){
            steps{
                sh 'ls'
            }
        }
        stage('voir stages'){
            steps{
                sh 'cat Jenkinsfile |grep stage'
            }
        }
    }
}