pipeline {
  agent any
  tools {
    maven "Maven"
  }
    stages {
        stage('build') {
            steps {
                echo 'build ...'
                sleep 5
            }
        }
        stage('test') {
            steps {
                echo 'test..'
                sleep 5
                //snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "test_artifact.jar","version": "1.${BUILD_NUMBER}","semanticVersion": "1.${BUILD_NUMBER}.0","repositoryName": "dev_artifact_repo"}]}""")
                //snDevOpsChange()
            }
        }
        stage('Deploy for development') {
            when {
                branch 'development'
            }
            steps {
                 echo 'dev branch deployment ..'
                 sleep 10
                 snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "dev_artifact.jar","version": "1.${BUILD_NUMBER}","semanticVersion": "1.${BUILD_NUMBER}.0","repositoryName": "dev_artifact_repo"}]}""")
                 //snDevOpsChange()
                
            }
        }
        stage('Deploy for production') {
            when {
                branch 'prod'  
            }
            steps {
                echo 'prod branch deployment …'
                sleep 5
            }
        }
    }
}
