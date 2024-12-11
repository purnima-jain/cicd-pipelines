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

        string(defaultValue: 'my-new-app', 
                description: '''<pre>Please refer below table for naming conventions <br/>
reports                           : wsit-od-reports-{name}
tpt                               : wsit-od-pymt-tpt-{name}
payments                          : wsit-od-pymt-{name}
entitlements & entl-rolemgmt      : wsit-od-entl-{name}
ccaas                             : wsit-od-ccaas-{name}
hbfr                              : wsit-od-hbfr-{name}
NOTE: application name should not exceed more than 40 characters</pre>''', 
                name: 'application_name', 
                trim: true),

        string(defaultValue: 'com.wf.wsit.od',
                description: '''<pre>API generated classes will use it as base package name
For busfunc it should be same as it's function name</pre>''', 
                name: 'package_name', 
                trim: true),

        [$class: 'CascadeChoiceParameter', 
            choiceType: 'PT_SINGLE_SELECT', 
            description: '''<pre>Select deployment template</br>
java-spring-boot                   : Java Spring Boot application on GKE
java-spring-boot-custom-truststore : Java Spring Boot application on GKE with Redis</pre>''', 
            filterLength: 1, 
            filterable: false, 
            name: 'helmChart', 
            randomName: 'choice-parameter-15543677788', 
            referencedParameters: 'templateType', 
            script: [
                $class: 'GroovyScript', 
                fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: ''], 
                script: [classpath:[], oldScript: '', sandbox: true, script: '''if(templateType.contains(\'api\')) {}
else if(templateType.contains(\'workflow\')) { return[\'sof\'] }'''
                        ]
            ]
        ],
        
        string(description: '''<pre>example: @test
NOTE: Testing tag will be used to run automated test suite during api promotion</pre>''', 
                name: 'testing_tag', 
                trim: true),
        
        booleanParam(description: 'Select to deploy internal kong proxy', name: 'internal'),

        booleanParam(description: '''<pre>Select to deploy external kong proxy
NOTE: For deployment of external proxy please connect with devops team or email requirements to crap@gmail.com</pre>''', 
                        name: 'external'),
        booleanParam(description: 'Select dsp for dibba', name: 'dibba_uk'),
        booleanParam(description: 'Select dsp for dibba', name: 'dibba_hk'),

        booleanParam(description: '''Select dsp for wfnet
        <hr><br>
        <pre>Please select platform specific properties</pre>''', 
                        name: 'wfnet'),

        extendedChoice(multiSelectDelimiter: ',', name: 'platform', quoteValue: false, saveJSONParameterToFile: false, type: 'PT_CHECKBOX', value: 'gcp, ikp', visibleItemCount: 5),
        extendedChoice(multiSelectDelimiter: ',', name: 'gcpRegion', quoteValue: false, saveJSONParameterToFile: false, type: 'PT_CHECKBOX', value: 'uk, hk', visibleItemCount: 5),
        extendedChoice(multiSelectDelimiter: ',', name: 'ikpRegion', quoteValue: false, saveJSONParameterToFile: false, type: 'PT_CHECKBOX', value: 'uk, hk', visibleItemCount: 5),
        choice(description: 'Select IKP Cluster', name: 'ikpClusterName', choices: ['ikp01', 'ikp02', 'ikp03'])
    ])
])


def githubCredentialId = 'opennet_tooling_git'
def devopsMetadataRepo = 'https://alm-giithub.systems.uk.wf/WSIT-OPENNET-DEVOPS/devops-metadata.git'
def devopsMetadataBranch = 'develop'
def jenkinsPath = 'https://almjenkinsci-prod.systems.uk.wf/wholeit03/job/hsbc-11858263-opennet/job/non-prod/job'
def jenkinsHostName = 'https://almjenkinsci-prod.systems.uk.wf'
def jenkinsCredentialsId = 'GB-ONET-TS-DEV'
def snapshot_job_to_run = 'hsbc-11858263-opennet/non-prod'
def jenkinTokenValue
def status
def url
def gitUrl
def namespace
def multiChannel
def busFunc
def ukDevProxyUrl
def hkDevProxyUrl
def dsp_dibba
def dsp_wfnet
def eimId
def platformList



pipeline {
    agent any

    stages {
        stage('Audit Tools') {
            steps {
                echo 'Inside Audit Tools....'
                auditTools()
            }
        }
        stage('api-onboarding') {
            steps {
                script {
                    ansiColor('xterm') {
                        echo "apiCodeConfig = ${apiCodeConfig}"
                        if("${apiCodeConfig}" == 'true') {
                            templateType = 'api-code-config'
                        }

                        echo "templateType = ${templateType}"
                        if(("${templateType}" == 'busfunc')) {
                            timeout(time: 600, unit: 'SECONDS') {
                                busFunc = input message: 'Please enter busfunc name', parameters: [string('Business Function Name')]

                                echo "busFunc = ${busFunc}"                                
                            }
                        }

                        

                        // Continue
                    }
                }
            }
        }
    }
}
