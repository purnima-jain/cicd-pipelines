pipeline {
    agent any

    stages {
        
        stage("Get First Name & Last Name") {
            steps {
                getName()
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

    echo "First Name :: " + name["firstName"]
    echo "Last Name :: " + name["lastName"]

    return name["firstName"] + " " + name["lastName"]
}

