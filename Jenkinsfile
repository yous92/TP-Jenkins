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
 
     stage('Code Quality') {
      
          steps {
            
             waitForQualityGate true
             
        }
     }


   
     stage('Build') {
     steps {
        bat'gradle build'
        bat 'gradle javadoc'
       archiveArtifacts 'build/libs/*.jar, build/docs/javadoc/*'
     }
       
         
     }
       
            stage('Publish') {
      steps {
        bat 'gradle publish'
      }
    }
    
    
    stage('Email notification') {
      steps {
            mail to: "ja_boucetta@esi.dz",
            subject: "Test Email",
            body: "Test"

      }
    }
    
    
    
  stage('Slack and msg Notifications') {
      steps {
        notifyEvents message: 'New build is created successfuly', token:'hBiYjwp3l4bS3IkjbcDmTC8vSsL1lVUs'
      }
    }
    

}

}
 
