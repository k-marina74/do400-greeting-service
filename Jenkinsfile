pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    oc project rqerwd-greetings
                    oc start-build greeting-service --follow --wait
                '''
            }
        }

        // Add the "Deploy" stage here
    }
}
