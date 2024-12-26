pipeline {
    agent any

    stages {
        
        stage("Get First Name & Last Name") {
            steps {
                script {
                    def name = getName()
                    echo "Name :: " + name                    // Name :: [firstName:Purnima, lastName:Jain]
                    echo "First Name :: " + name["firstName"] // First Name :: Purnima
                    echo "Last Name :: " + name["lastName"]   // Last Name :: Jain
                }
            }           
        }
        
    }
}

Map getName() {    
    def name = input message: "Enter Name",
                        parameters: [
                            string(name: 'firstName', description: 'First Name', defaultValue: ''),
                            string(name: 'lastName', description: 'Last Name', defaultValue: '')
                        ]

    echo "First Name :: " + name["firstName"]  // First Name :: Purnima
    echo "Last Name :: " + name["lastName"]    // Last Name :: Jain

    return name
}

