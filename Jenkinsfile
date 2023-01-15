pipeline {
  agent any
  stages {
    stage('Test'){
      steps{
      bat "gradle test" 
      archiveArtifacts 'build/test-results/test/*'
      cucumber 'reports/*.json'
   
      }
      
      
      
    }
    
    stage('Code Analysis') {
          steps {
             withSonarQubeEnv('sonar') {
              bat 'gradle sonarqube '
            }

          
          }
        }
    
//      stage('Code Quality') {
//           steps {
//             waitForQualityGate true
          
//           }
//         }
    
     stage('Build') {
     steps {
        bat'gradle build'
        bat 'gradle javadoc'
       archiveArtifacts 'build/libs/*.jar, build/docs/javadoc/*'
     }
       
        
     }
}

}
