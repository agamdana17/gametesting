pipeline {
  agent none
  stages {
    
    stage ('Checkout'){
      agent{ label 'Windows'}
      steps {
        git branch: 'main',
          credetntialsId:'github-token',
          url: 'https://github.com/agamdana17/GameTesting.git'
      }
    }

    stage ('Run Unity NUnit Test'){
      agent{ label 'Windows'}
      steps {
        bat "\""C:\\Program Files\\Unity\\Hub\\Editor\\6000.0.47f1\\Editor\\Unity.exe" -runTest -projectPath" -testResultsFormatNunit -testPlatform -batchmode -quit"
      }
    }

    stage ('Publish NUnit Results'){
      agent{ label 'Windows'}
      steps {
        nunit testResultsPattern: 'Assets\Tests\TestResults.xml'
      }
    }
    
  }
}
