pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true 
                }
            }
            steps {
                sh'''
                ls -la
                '''
            }
        }
    }
   
        stage('Test') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true 
                }
            }
            steps {
                sh'''
             
                touch index.html
                npm test
                '''
            }
        
    }
}
