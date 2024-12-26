pipeline {
    agent any

    stages {
        stage("Accessing Variables defined inside Script block ....") {
            steps {
                script {
                    def responseDef = input message: 'Enter Name', 
                        parameters: [string(name: 'firstName', description: 'Enter First Name', defaultValue: '')]
                    
                    env.responseEnv = input message: 'Enter Name', 
                        parameters: [string(name: 'lastName', description: 'Enter Last Name', defaultValue: '')]

                    echo "First Name is " + responseDef["firstName"]
                    echo "Last Name is " + responseEnv["lastName"]
                }
                echo "First Name is " + responseDef["firstName"]
                echo "Last Name is " + responseEnv["lastName"]
                echo "Last Name is " + env.responseEnv["lastName"]
                echo "Last Name is ${env.responseEnv['lastName']}"
            }
        }
    }
}



