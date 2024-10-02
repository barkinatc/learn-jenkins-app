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
                npm install serve
                node_modules/.bin/serve -s build &
                sleep 10
                npx playwright test --reporter=line
                '''
            }
        }
    }
    post{
        always{
           junit 'jest-results/junit.xml'
        }
    }
}
