pipeline {
  agent any
  tools {
    maven "Maven"
  }
    stages {
        stage('build') {
            steps {
                echo 'build ..'
                sleep 5
            }
        }
        stage('test') {
            steps {
                echo 'test .'
                sleep 5

            }
        }
        stage('Deploy for development') {
            when {
                branch 'development'
            }
            steps {
                 echo 'dev branch deployment ...'
                sleep 5
            }
        }
        stage('Deploy for production') {
            when {
                branch 'prod'  
            }
            steps {
                echo 'prod branch deployment .'
                sleep 5
            }
        }
    }
}
