#!/usr/bin/env groovy
@Library('cicd-shared-library') _
properties(
    [
        [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], 
        parameters(
            [
                [$class: 'ChoiceParameter', 
                    choiceType: 'PT_RADIO', 
                    filterLength: 1, 
                    filterable: false, 
                    name: 'configChange', 
                    randomName: 'choice-parameter-22391555645786788', 
                    script: [$class: 'GroovyScript', 
                                fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: ''], 
                                script: [classpath: [], ooldScript: '', sandbox: true, script: 'return[\'true\', \'false:selected\']']
                            ]
                ], 
                [$class: 'CascadeChoiceParameter', 
                    choiceType: 'PT_RADIO', 
                    filterLength: 1, 
                    filterable: false, 
                    name: 'executeSast', 
                    randomName: 'choice-parameter-2239155354776789', 
                    referencedParameters: 'configChange', 
                    script: [$class: 'GroovyScript', 
                                fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: ''], 
                                script:[classpath: [], oldScript: '', sandbox: true, script: '''if (configChange.equals("false")) {
return [
\'true\',
\'false:selected\'
]
}
else
return[
\'true:disabled\',
\'false:selected\'
]
''']
                            ]
                ]
            ]
        ), 
        [$class: 'JobLocalConfiguration', changeReasonComment: '']
    ]
)

params = [
    devopsMetadataRepo: 'https://github.com/purnima-jain/cicd-metadata.git',
    devopsMetadataBranch: 'master',
    helmChartGitRepo: 'https://github.com/purnima-jain/helm-chart.git',
    helmChartVersion: 'master',
    nexusCredId: 'NEXUS_CRED_ID',
    githubCredentialsId: 'GITHUB_CREDENTIAL_ID',
    configChange: configChange,
    executeSast: executeSast
]

pipelineJavaMain(params)