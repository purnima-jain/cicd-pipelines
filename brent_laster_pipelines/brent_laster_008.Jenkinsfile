def name

pipeline {
    agent any

    stages {
        
        stage("Defining a variable outside pipeline") {
            steps {
                script {
                    name = input message: "Enter Name",
                        parameters: [
                            string(name: 'firstName', description: 'First Name', defaultValue: ''),
                            string(name: 'lastName', description: 'Last Name', defaultValue: '')
                        ]                    
                }
                echo "Name :: " + name  // Name :: [firstName:Purnima, lastName:Jain] 
            }           
        }
        
    }
}



