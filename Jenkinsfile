pipeline {
  agent any
  stages{
     stage ('test') {
      steps{
          bat 'gradle test'
          archiveArtifacts 'build/test-results/'
      }
    }
  
}
}
