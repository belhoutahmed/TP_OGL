pipeline {
  agent any
  stages{
    stage ('test'){
      steps{
        bat 'gradle build'
        archiveArtifacts 'build/test-results/'
        
      }
    }
  
}

}
