pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
    stages{
        stage('user'){
            steps{
                sh 'who'
            }
         }
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
        stage('check pwd'){
            steps{
                sh 'pwd'
            }
        }
       
        stage('upload artifact'){
            steps{
                script{
                def mavenPom = readMavenPom file: 'pom.xml'
                nexusArtifactUploader artifacts: [[artifactId: "${mavenPom.artifactId}",
                 classifier: '',
                  file: "target/${mavenPom.artifactId}-${mavenPom.version}.${mavenPom.packaging}",
                   type: "${mavenPom.packaging}"]],
                    credentialsId: 'NexusID',
                     groupId: "${mavenPom.groupId}",
                      nexusUrl: '170.187.193.86:8081',
                       nexusVersion: 'nexus3',
                        protocol: 'http',
                         repository: 'bio-medical-app',
                          version: "${mavenPom.version}"
                }
            }
                
        }

    }
}