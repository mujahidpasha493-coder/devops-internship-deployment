pipeline {
agent any

stages {
    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Validate') {
        steps {
            sh 'test -f index.html && test -f Dockerfile'
        }
    }

    stage('Build') {
        steps {
            sh 'docker build -t internship-web:latest .'
        }
    }

    stage('Deploy') {
        steps {
            sh '''
                docker rm -f internship-web || true
                docker run -d --name internship-web \
                  --restart unless-stopped -p 80:80 internship-web:latest
            '''
        }
    }

    stage('Verify') {
        steps {
            sh 'curl --fail http://localhost/'
        }
    }

    stage('Cleanup') {
        steps {
            sh 'docker image prune -f'
        }
    }
}

}
