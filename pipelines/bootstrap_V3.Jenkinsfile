library identifier: 'cicd-shared-library@master',
        retriever: modernSCM([
            $class: 'GitSCMSource', 
            branches: [[name: 'master']]
            remote: 'https://github.com/purnima-jain/cicd-shared-library.git'
        ])

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