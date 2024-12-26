pipeline {
    agent any

    stages {

        stage("Checking to continue....") {
            steps {
                input message: "Continue to next Stage?"
                echo "******************************************"
            }
        }
        
        stage("Catching the approver....") {
            steps {
                script {
                    def response = input message: "Continue to next Stage?",
                        ok: "Yes, please!!",
                        submitter: "admin,JohnDoe", // admin and JohnDoe are usernames
                        submitterParameter: "approver" // This is required even though not directly using it
                    
                    echo "Approved by ${response}" // Approved by admin
                    echo "Approved by $response"   // Approved by admin
                    echo "Approved by " + response // Approved by admin
                    
                    // echo "Approved by " + approver             // Error
                    // echo "Approved by " + $approver            // Error
                    // echo "Approved by " + $response.approver   // Error              
                    // echo "Approved by " + response['approver'] // Error
                    echo "******************************************"
                }                
            }
        }

        stage("Capturing the String input....") {
            steps {
                script {
                    def response = input message: "Continue to deploy?",
                        ok: "Yes, please!!",
                        submitter: 'admin,JohnDoe',
                        submitterParameter: "approver",
                        parameters: [string(defaultValue: 'PROD', description: 'Environment to deploy to ', name: 'environment')]
                    
                    echo "Environment to be deployed to $response"                  // Environment to be deployed to 
                                                                                    //      [approver:admin, environment:PROD]
                    echo "Environment to be deployed to ${response['environment']}" // Environment to be deployed to PROD
                    echo "Environment to be deployed to $response['environment']"   // Environment to be deployed to 
                                                                                    //      [approver:admin, environment:PROD]['environment']
                    echo "Environment to be deployed to " + response["environment"] // Environment to be deployed to PROD
                }                
            }
        }
    }
}