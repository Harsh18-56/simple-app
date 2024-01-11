pipeline {
    agent any
    tools {
        maven 'maven1'
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean'
            }
        }
        stage('Upload War To Nexus'){
            steps{
                script{
                    readProp = readProperties File: 'simple-app.properties'
                }
                nexusArtifactUploader artifacts: [
                        [
                            artifactId: '**/target/*.war', 
                            classifier: '', 
                            file: '', 
                            type: 'war'
                        ]
                    ], 
                  credentialsId: 'Nexus3', 
                  groupId: 'in.javahome', 
                  nexusUrl: '65.0.73.39:8081', 
                  nexusVersion: 'nexus3', 
                  protocol: 'http', 
                  repository: 'testrepo', 
                  version: '3.0.5'
               }
            }
        }
   }
    

