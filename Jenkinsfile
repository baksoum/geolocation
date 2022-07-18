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
       
        stage('upload artifact'){
            steps{
                script{
                def mavenPom = readMavenPom file: 'pom.xml'
                nexusArtifactUploader artifacts: [[artifactId: "${POM_ARTIFACTID}",
                 classifier: '',
                  file: "target/${POM_ARTIFACTID}-${POM_VERSION}.${POM_PACKAGING}",
                   type: "${POM_PACKAGING}"]],
                    credentialsId: 'NexusID',
                     groupId: "${POM_GROUPID}",
                      nexusUrl: '170.187.193.86:8081',
                       nexusVersion: 'nexus3',
                        protocol: 'http',
                         repository: 'bio-medical-app',
                          version: "${POM_VERSION}"
                }
            }
                
        }
    }
}