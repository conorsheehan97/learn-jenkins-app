pipeline {

    agent any 
    stages {
        stage('Build'){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                ls -la
                node --version
                npm --version
                npm ci 
                npm run build
                ls -la
                '''
            }
        
        }
        stage('Test')
        {
            agent {
                  docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
                steps{
                    sh'''
                    if [ -f /build/index.html ]; then
    echo "File exists and is a regular file."
else
    echo "File does not exist or is not a regular file."
fi

                    '''
                }

        }
    }
}