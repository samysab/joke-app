pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
              sh "node -v"
                sh 'npm i -g pnpm'
                sh "pnpm install"
                sh "pnpm build"
                sh "pnpm test"
            }
        }
    }
}
