pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: 'Node 6.x', configId: '18') {
                    sh 'npm config ls'
                    sh "npm install"
                    sh "npm run build"
                    sh "npm test"
                }
            }
        }
    }
}
