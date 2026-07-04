pipeline {
    agent any
    stages {
        stage('Build DImage'){
            steps {
                echo 'Building Image'
                sh 'docker build -t practiceimg:${BUILD_NUMBER} .'
            }
        }

        stage('Tagging image'){
            steps{
                sh 'docker tag practiceimg:${BUILD_NUMBER} banturamya/practiceimg:${BUILD_NUMBER}'
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
            docker push $USER/practiceimg:${BUILD_NUMBER}
            '''
        }
        }
        }
        stage('run image'){
            steps{
                echo 'running image'
                sh 'docker run -d --name practimg -p 8083:80 banturamya/practiceimg:${BUILD_NUMBER}'
            }
        }
        
    }

}