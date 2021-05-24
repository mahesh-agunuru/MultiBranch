pipeline {
  agent any
  tools {
    maven "Maven"
  }
    stages {
        stage('build') {
            steps {
                echo 'build... '
                sleep 5
            }
        }
        stage('test') {
            steps {
                echo 'test ..'
                sleep 5
                //snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "test_artifact.jar","version": "1.${BUILD_NUMBER}","semanticVersion": "1.${BUILD_NUMBER}.0","repositoryName": "test_artifact_repo"}]}""")
                snDevOpsChange()
            }
        }
        stage('Deploy for development') {
            when {
                branch 'development'
            }
            steps {
                 echo 'dev branch deployment ..'
                sleep 5
            }
        }
        stage('Deploy for production') {
            when {
                branch 'prod'  
            }
            steps {
                echo 'prod branch deployment .'
                snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "prod_artifact.jar","version": "1.${BUILD_NUMBER}","semanticVersion": "1.${BUILD_NUMBER}.0","repositoryName": "prod_artifact_repo"}]}""")
                sleep 5
            }
        }
    }
}
