pipeline {
    agent any

    stages {
        stage("Accessing Variables defined inside Script block ....") {
            steps {
                script {
                    
                    env.name = input message: "Enter Name",
                        parameters: [
                            string(name: 'firstName', description: 'First Name', defaultValue: ''),
                            string(name: 'lastName', description: 'Last Name', defaultValue: '')
                        ]

                    echo "*env.name :: ${env.name}"
                    echo "**env.name :: ${env.name.firstName}"
                    echo "***env.name :: ${env.name.lastName}"
                    echo "****env.name :: ${env.name.lastName}"
                    echo "*****env.name :: " + env.name['firstName']
                    echo "******env.name :: " + env.name['lastName']
                }

                echo "******************************************"
                echo "*env.name :: ${env.name}"
                echo "**env.name :: ${env.name.firstName}"
                echo "***env.name :: ${env.name.lastName}"
                echo "****env.name :: ${env.name.lastName}"
                echo "*****env.name :: " + env.name['firstName']
                echo "******env.name :: " + env.name['lastName']

            }
        }
    }
}



