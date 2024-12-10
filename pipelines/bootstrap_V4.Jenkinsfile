library identifier: 'cicd-shared-library@master',
        retriever: modernSCM([
            $class: 'GitSCMSource', 
            remote: 'https://github.com/purnima-jain/cicd-shared-library.git'
        ])

properties([
    parameters([
        choice(choices: ['api', 'workflow', 'busfunc'], name: 'templateType'),
        booleanParam(description: 'Select checkbox for Single Code & Config repo', name: 'apiCodeconfig'),
        choice(choices: ['payments', 'entitlements', 'entl-rolemgmt', 'ccaas', 'hbfr', 'reports', 'tpt'], name: 'domainConfiguration'),
        string(defaultValue: 'my-new-app', description: '''<pre>Please refer below table for naming conventions <br/>
reports                           : wsit-od-reports-{name}
tpt                               : wsit-od-pymt-tpt-{name}
payments                          : wsit-od-pymt-{name}
entitlements & entl-rolemgmt      : wsit-od-entl-{name}
ccaas                             : wsit-od-ccaas-{name}
hbfr                              : wsit-od-hbfr-{name}
NOTE: application name should not exceed more than 40 characters</pre>''', name: 'application_name', trim: true),
        string(defaultValue: 'com.purnima.wsit.od', description: '''<pre>API generated classes will use it as base package name
For busfunc it should be same as it's function name</pre>''', name: 'package_name', trim: true)
       
        
    ])
])
       

pipeline {
    agent any

    stages {
        stage('Audit Tools') {
            steps {
                echo 'Inside Audit Tools....'
                auditTools()
            }
        }
    }
}
