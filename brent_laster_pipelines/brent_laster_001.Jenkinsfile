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
                    echo "******************************************"
                }                
            }
        }

        stage("Capturing Boolean input....") {
            steps {
                script {
                    def response = input message: "Do you want to deploy?",
                        ok: "Yes",
                        parameters: [booleanParam(defaultValue: true, description: 'Deploy?', name: 'isDeploy')]
                    
                    echo "Do you want to deploy? $response"                     // Do you want to deploy? true
                    // echo "Do you want to deploy? ${response['isDeploy']}"    // Error
                    // echo "Do you want to deploy? " + response["isDeploy"]    // Error
                    echo "******************************************"
                }                
            }
        }

        stage("Capturing Boolean & String input....") {
            steps {
                script {
                    def response = input message: "Input Values:",
                        parameters: [
                            booleanParam(defaultValue: true, description: 'Deploy?', name: 'isDeploy'),
                            string(defaultValue: 'PROD', description: 'Environment to deploy to ', name: 'environment')
                        ]                        
                    
                    echo "response :: " + response                     // response :: [environment:PROD, isDeploy:true]
                    echo "response :: $response"                       // response :: [environment:PROD, isDeploy:true]
                    echo "environment :: " + response["environment"]   // environment :: PROD
                    echo "isDeploy :: " + response["isDeploy"]         // isDeploy :: true           
                    echo "******************************************"
                }                
            }
        }

        stage("Capturing Choice & Multi-line input....") {
            steps {
                script {
                    def response = input message: "Input Values:",
                        parameters: [
                            choice(name: 'environment', description: 'Select Deployment Environment', 
                                    choices: ['dev', 'uat', 'pre-prod', 'prod']),
                            text(name: 'comment', description: 'Enter comment', defaultValue: '''This
is a
multiline comment'''
                            )
                        ]                        
                    
                    echo "response :: " + response // response :: [environment:uat, comment:This\nis a\nmultiline comment]
                    echo "response :: $response"   // response :: [environment:uat, comment:This\nis a\nmultiline comment]
                    echo "environment :: " + response["environment"] // environment :: uat
                    echo "comment :: " + response["comment"]         // comment :: This\nis a\nmultiline comment      
                    echo "******************************************"
                }                
            }
        }

        stage("Capturing Username & Password....") {
            steps {
                script {
                    def loginInfo = input message: "Login:",
                        parameters: [
                            string(name: 'username', description: 'Enter Username', defaultValue: ''),
                            password(name: 'password', description: 'Enter Password', defaultValue: ''),
                        ]                        
                    
                    echo "Username :: " + loginInfo['username']
                    echo "Username :: " + loginInfo.username
                    echo "Password :: ${loginInfo['password']}"
                    echo "Password :: " + loginInfo.password
                    echo "******************************************"
                }                
            }
        }
    }
}