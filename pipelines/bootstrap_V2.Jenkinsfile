pipeline {
    agent any

    stages {
        stage('Audit Tools') {
            steps {
                echo 'Inside Audit Tools....'
                auditTools()
            }
        }
    }
}

void auditTools() {
    sh '''
        git version
        docker version
        java --version
        mvn --version
    '''
}