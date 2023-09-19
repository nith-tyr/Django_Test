pipeline {
    
    agent any 
    
    environment {
        IMAGE_TAG = "${BUILD_NUMBER}"
    }
    
    stages {
        
        stage('Checkout'){
           steps {
                git credentialsId: '619efdce-e8a7-406c-ac25-2cca72506561', 
                url: 'https://github.com/nith-tyr/Django_Test.git', 
                branch: 'main'
           }
        }

        stage('Build Docker'){
            steps{
                script{
                    sh '''
                    echo 'Buid Docker Image'
                    docker build -t nitheeshbp/cicd-e2e:${BUILD_NUMBER} .
                    '''
                }
            }
        }

        stage('Push the artifacts'){
           steps{
                script{
                    sh '''
                    echo 'Push to Repo'
                    docker push nitheeshbp/cicd-e2e:${BUILD_NUMBER}
                    '''
                }
            }
        }
        
       
        }
    }
}
