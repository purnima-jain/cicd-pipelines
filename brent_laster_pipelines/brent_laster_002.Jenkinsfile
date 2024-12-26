properties ([
    parameters ([
        string(name: "firstName", description: "Enter First Name", defaultValue: '')
    ])
])

pipeline {
    agent any

    parameters {
        string(name: "lastName", description: "Enter Last Name", defaultValue: '')
    }

    stages {
        stage("Printing Proporties-Level & Pipeline-Level Parameters....") {
            steps {
                echo "First Name is " + params.firstName     // First Name is Jane
                echo "First Name is ${params.firstName}"     // First Name is Jane
                echo "First Name is $params.firstName"       // First Name is Jane
                echo "First Name is " + params['firstName']  // First Name is Jane
                echo "******************************************"
                echo "Last Name is " + params.lastName       // Last Name is Doe
                echo "Last Name is ${params.lastName}"       // Last Name is Doe
                echo "Last Name is $params.lastName"         // Last Name is Doe
                echo "Last Name is " + params['lastName']    // Last Name is Doe
            }
        }
    }
}



