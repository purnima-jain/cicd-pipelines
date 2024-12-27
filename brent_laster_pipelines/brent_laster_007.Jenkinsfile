pipeline {
    agent any

    stages {
        
        stage("Input within the specified timeout") {
            steps {
                script {
                    timeout(time: 10, unit: 'SECONDS') {
                        def name = input message: "Enter Name",
                        parameters: [
                            string(name: 'firstName', description: 'First Name', defaultValue: ''),
                            string(name: 'lastName', description: 'Last Name', defaultValue: '')
                        ]
                        echo "Name :: " + name  // Name :: [firstName:Purnima, lastName:Jain]                       
                    }
                    
                }
            }           
        }
        
    }
}



