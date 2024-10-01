pipeline {
    agent any

    stages {
        
        
        /*
        
        
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo 'lol'
                '''
            }
        }
        */
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo TEST STAGE
                touch build/index.html
                
                '''
            }
        }
         stage('E2E') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.47.2-noble'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo ECHO E2E
                npm install -g serve
                serve -s build
                npx playwright test
                '''
            }
        }
    }
    post{
        always{
            junit 'test-results/junit.xml'
        }
    }
}
