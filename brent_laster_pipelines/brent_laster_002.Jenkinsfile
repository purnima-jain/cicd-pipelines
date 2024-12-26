pipeline {
    agent any

    parameters {
        string(name: "firstName", description: "Enter First Name", defaultValue: '')
    }

    stages {

        stage("Printing Pipeline-Level Parameter....") {
            steps {
                echo "First Name is " + params.firstName
                echo "First Name is ${params.firstName}"
                echo "First Name is $params.firstName"
                echo "First Name is " + params['firstName']
                echo "******************************************"
            }
        }
        
    }
}