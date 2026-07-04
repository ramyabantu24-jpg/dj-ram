pipeline {
    agent any
    stages {
        stage('Build DImage'){
            steps {
                echo 'Building Image'
                sh 'docker build -t r-dj:v1 .'
            }
        }
    }

}