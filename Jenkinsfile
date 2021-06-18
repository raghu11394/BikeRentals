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
           }
          post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
          }
        }     
  }
}
