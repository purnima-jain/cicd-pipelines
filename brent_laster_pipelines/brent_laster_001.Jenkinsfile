pipeline {
    agent any

    stages {
        
        stage("Checking to continue....") {
            steps {
                def response = input 
                    message: "Continue to next Stage?",
                    ok: "Yes, please!!",
                    submitter: 'admin,JohnDoe', // admin and JohnDoe are usernames
                    submitterParameter: "approver"
                
                echo "Approved by ${response}"
                echo "Approved by $response"
                echo "Approved by " + response
                echo "Approved by " + response[approver]
            }
        }
    }
}