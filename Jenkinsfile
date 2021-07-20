//currentBuild.displayName = "BikeRental"+"#${BUILD_NUMBER}"

pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("Build_NewB") {
                steps {
                    echo "Building" 
                    sh 'mvn -X clean install -DskipTests'
                }
       }
        stage("Test_NewB") {
           steps {
               echo "Testing"
               sh 'mvn test'
               snDevOpsArtifact(artifactsPayload:"""
               {"artifacts": 
                  [
                     {
                        "name": "TestArtifact",
                        "version":"0.${env.BUILD_NUMBER}.0",
                        "semanticVersion": "0.${env.BUILD_NUMBER}.0",
                        "repositoryName": "bm-artifacts-repo"
                       }
                    ]
                 }""")
           }
          post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
          }
        }     
  }
}
