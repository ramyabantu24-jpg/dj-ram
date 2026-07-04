pipeline {
    agent any
    stages {
        stage('Build DImage'){
            steps {
                echo 'Building Image'
                sh 'docker build -t r-dimage:v1 .'
            }
        }

        stage('Tagging image'){
            steps{
                sh 'docker tag r-dimage:v1 banturamya/r-dimage:v1'
            }
        }

        stage('push'){
            steps{
            echo 'pushing image'
            withCredentials([
                usernamePassword(
                credentialsId: 'docker-cred',
                usernameVariable: 'USER',
                passwordVariable: 'PASS'
                )
        ]){
            sh '''
            docker login -u $USER -p $PASS
            docker push banturamya/r-dimage:v1
            '''
        }
        }
        }
        
    }

}