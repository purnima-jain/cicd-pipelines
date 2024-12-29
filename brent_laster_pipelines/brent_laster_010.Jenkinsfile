library identifier: 'cicd-shared-library@master', 
      retriever: modernSCM([$class: 'GitSCMSource', 
                           remote: 'https://github.com/purnima-jain/cicd-shared-library.git'])

pipeline {
    agent any	

    stages {
        
        stage("Hello from Pipeline...") {
            steps {
                echo "Hello from Pipeline"
                helloFromVars("Hello from vars directory....")
            } 
        }

    }
}