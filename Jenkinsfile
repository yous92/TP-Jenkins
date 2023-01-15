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
    
//     stage('Code Analysis') {
      
      
  
//           steps {
//             withSonarQubeEnv('sonar') {
//               bat(script: 'D:\\gradle-5.6\\bin\\gradle sonarqube', returnStatus: true)
//             }

          
//           }
//         }
    
//      stage('Build') {
//      steps {
//         bat(script: 'gradle build', label: 'gradle build')
//         bat 'gradle javadoc'
//        archiveArtifacts 'build/libs/*.jar, build/docs/javadoc/*'}
       
        
//      }
}

}
