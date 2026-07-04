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
    }

}