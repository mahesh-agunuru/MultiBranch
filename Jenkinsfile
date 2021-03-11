pipeline {
  agent any
  tools {
    maven "Maven"
  }
    stages {
        stage('build') {
            steps {
                echo 'build ...'
                 snDevOpsStep()
                sleep 5
            }
        }
        stage('test') {
            steps {
                echo 'test .'
                 snDevOpsStep()
                sleep 5
                //snDevOpsChange()
            }
        }
        stage('Deploy for development') {
            when {
                branch 'development'
            }
            steps {
                 echo 'dev branch deployment ...'
                 snDevOpsStep()
              sleep 10
              snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "development_artifact.jar","version": "1.0","semanticVersion": "1.0.0","repositoryName": "development_artifact_repo"}],"stageName": "Deploy for development"}""")
                
            }
        }
        stage('Deploy for production') {
            when {
                branch 'prod'  
            }
            steps {
                echo 'prod branch deployment .'
                 snDevOpsStep()
                sleep 5
            }
        }
    }
}
