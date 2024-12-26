pipeline {
    agent any

    stages {
        
        stage("Get First Name & Last Name without script block") {
            steps {
                // def name = getName() // Error
                echo "*Name :: " + getName() // *Name :: Purnima Jain
                echo "******************************************"
            }           
        }

        stage("Get First Name & Last Name with script block") {
            steps {
                script {
                    def name = getName()
                    echo "**Name :: " + name // **Name :: Purnima Jain
                    echo "******************************************"
                }
            }           
        }
        
    }
}

String getName() {    
    def name = input message: "Enter Name",
                        parameters: [
                            string(name: 'firstName', description: 'First Name', defaultValue: ''),
                            string(name: 'lastName', description: 'Last Name', defaultValue: '')
                        ]

    echo "First Name :: " + name["firstName"]  // First Name :: Purnima
    echo "Last Name :: " + name["lastName"]    // Last Name :: Jain

    return name["firstName"] + " " + name["lastName"]
}

