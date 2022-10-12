pipeline {
    agent any

    parameters {
        choice(name: 'NODE_VERSION', choices: ['18', '17'])
    }

    environment {
        tag = "registry.heroku.com/jokeappli/web"
    }

    stages {
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: "${params.NODE_VERSION}") {
                    sh 'npm config ls'
                    sh "npm install"
                    sh "npm run build"
                    sh "npm test"
                }
            }
        }

        stage('deploy'){
            steps{
                script {
                    docker.withRegistry('https://registry.heroku.com', 'herokuid') {
                        def image = docker.build("${env.tag}")
                        image.push()
                    }
                }

                withCredentials([usernamePassword(credentialsId: 'herokuid', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh "HEROKU_API_KEY=${PASSWORD} npx heroku container:release web --app=jokeappli"
                }
            }
        }
    }
}
