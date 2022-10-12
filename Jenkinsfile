pipeline {
    agent any

    parameters {
        choice(name: 'NODE_VERSION', choices: ['18', '17'])
    }

    stages {
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: '${params.NODE_VERSION}') {
                    sh 'npm config ls'
                    sh "npm install"
                    sh "npm run build"
                    sh "npm test"
                }
            }
        }
    }
}
