pipeline {
    agent any

    tools {
        maven 'Maven'
    }
    
    stages {
        stage ('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/rochith11/MyMavenWebApp_test.git'
            }
        }
        stage ('Build')  {
            steps {
                sh 'mvn clean install'
            }
        }
        stage ('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprints=true
            }
        }
        stage ('Deploy') {
            steps { 
                'mvn clean package'
            }
        }
    }
    post {
        success {
            echo "Build Successful"
        }
        failure {
            echo "Build Failed"
        }
    }
}