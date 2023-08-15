pipeline {

    agent { node { label 'workstation' } }

    stages {
        stage('Helloo-1') {
            steps {
                echo 'Hello World'
            }
        }
    post {
        always
            sh 'echo post'
        }
    }
}
