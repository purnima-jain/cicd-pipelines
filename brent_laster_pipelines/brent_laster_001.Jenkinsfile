pipeline {
    agent any

    stages {

        stage("Checking to continue....") {
            steps {
                input message: "Continue to next Stage?"
            }
        }
        
        stage("Catching the approver....") {
            steps {
                script {
                    def response = input message: "Continue to next Stage?",
                        ok: "Yes, please!!",
                        submitter: 'admin,JohnDoe' // admin and JohnDoe are usernames
                        submitterParameter: "approver"
                    
                    echo "Approved by ${response}" // Approved by admin
                    echo "Approved by $response"   // Approved by admin
                    echo "Approved by " + response // Approved by admin
                    echo "******************************************"
                    // echo "Approved by " + approver // Error: MissingPropertyException: No such property: approver for class: groovy.lang.Binding
                    // echo "Approved by " + $approver // Error: MissingPropertyException: No such property: $approver for class: groovy.lang.Binding
                    // echo "Approved by " + $response.approver // Error: MissingPropertyException: No such property: $response for class: groovy.lang.Binding                  
                    // echo "Approved by " + response['approver'] // Error!! Requires script approval
                }                
            }
        }


    }
}