pipeline {
  agent any
  stages{
     stage ('test') {
      steps{
          bat 'gradle test'
        cucumber reportTitle: 'Report',
                   fileIncludePattern: 'target/report.json',
                   trendsLimit: 10
          junit 'build/test-results/test/TEST-Matrix.xml'
    
      }
    }
  
}
}
