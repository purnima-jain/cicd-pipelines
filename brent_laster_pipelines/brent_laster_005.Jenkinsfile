pipeline {
    agent any

    stages {
        
        stage("Get First Name & Last Name") {
            steps {
                def name = getName()
                echo "**********"
                echo "Name :: " + $name
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

