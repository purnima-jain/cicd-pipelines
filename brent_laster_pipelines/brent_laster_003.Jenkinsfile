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

                    echo "* First Name is " + responseDef
                    echo "** Last Name is " + responseEnv
                }
                // echo "First Name is " + responseDef["firstName"] // Error
                // echo "Last Name is " + responseEnv["lastName"] // Error
                echo "*** Last Name is " + responseEnv // Last Name is Jain
                // echo "Last Name is " + responseEnv["lastName"] // Error
                echo "**** Last Name is " + env.responseEnv // Last Name is Jain
                // echo "Last Name is " + env.responseEnv["lastName"] // Error
                echo "***** Last Name is ${env.responseEnv['lastName']}" // Error
            }
        }
    }
}



