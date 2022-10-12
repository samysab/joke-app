pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: '18') {
                    sh 'npm config ls'
                    sh "npm install"
                    sh "npm run build"
                    sh "npm test"
                }
            }
        }
    }
}
