#!/usr/bin/env groovy
library identifier: 'cicd-shared-library@master', 
      retriever: modernSCM([$class: 'GitSCMSource', 
                           remote: 'https://github.com/purnima-jain/cicd-shared-library.git'])

properties(
    [
        //[$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], 
        parameters(
            [
                [$class: 'ChoiceParameter', 
                    choiceType: 'PT_RADIO', 
                    filterLength: 1, 
                    filterable: false, 
                    name: 'configChange', 
                    randomName: 'choice-parameter-2239155532490562', 
                    script: [$class: 'GroovyScript', 
                                fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: ''], 
                                script: [classpath: [], oldScript: '', sandbox: true, script: 'return[\'true\', \'false:selected\']']
                            ]
                ], 
                [$class: 'CascadeChoiceParameter', 
                    choiceType: 'PT_RADIO', 
                    filterLength: 1, 
                    filterable: false, 
                    name: 'executeSast', 
                    randomName: 'choice-parameter-2239155535307950', 
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
        )// , 
        // [$class: 'JobLocalConfiguration', changeReasonComment: '']
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