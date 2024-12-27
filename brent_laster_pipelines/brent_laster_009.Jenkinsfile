def name

pipeline {
    agent any	

    stages {
        
        stage("Try Catch...") {
            steps {
                try {
                    timeout(time: 10, unit: 'SECONDS') {
                        name = input message: "Enter Name",
                        parameters: [
                            string(name: 'firstName', description: 'First Name', defaultValue: ''),
                            string(name: 'lastName', description: 'Last Name', defaultValue: '')
                        ]
                    }
                } 
                catch (err) {
                    name = "Jane Doe"
                }
                echo "Name :: " + name
            } 
        }
    }
}