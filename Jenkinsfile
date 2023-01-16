pipeline {
  agent any
  stages {
     stage ('test') {
      steps{
            bat 'gradle test'
             archiveArtifacts 'build/test-results/'
          cucumber reportTitle: 'Report',
                   fileIncludePattern: 'target/report.json',
                   trendsLimit: 10
          junit 'build/test-results/test/TEST-Matrix.xml'
      }
    }
    stage('code analyse'){
      steps{
        withSonarQubeEnv('sonar') {
          bat "gradle sonarqube"
        }
      }
    }
    stage("code quality") {
      steps {
          waitForQualityGate abortPipeline: true
      }
    }
    stage("build") {
      steps {
          bat "gradle build"
          bat "gradle javadoc"
          archiveArtifacts 'build/libs/*.jar'
          archiveArtifacts 'build/docs/'
      }
    }
    stage("deployement") {
      steps  {
          bat "gradle publish" 
      } 
    }  
    stage("notification") {
      steps {
          notifyEvents message: 'hi its me', token: 'TmeIlBZBNgWd1uKf8p2OdNWlBagvvKyc'
      }
    }
    
  }
  post {
        failure {
            mail bcc: '', body: '''Failure''', cc: '', from: '', replyTo: '', subject: 'Error', to: 'ja_belhout@esi.dz'
        } 
  }
 }

