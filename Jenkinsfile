pipeline {
    agent { label 'MASTER' }
        parameters {
            string(defaultValue: "prod_was_inventory", description: 'Ansible Host file', name: 'INV_FILE')
            string(defaultValue: "AA-PROD-WAS", description: 'Ansible Host Group', name: 'INV_GRP')   
            // choice(choices: ['DEV', 
            //             'DEV1', 
            //             'DEV2', 
            //             'DEV3', 
            //             'DEV4', 
            //             'DEV5', 
            //             'DEV6',
            //             'DEV5',
            //             'PERF',
            //             'PROD',
            //             'SEC',
            //             'SIT',
            //             'UAT',
            //             'UAT2',
            //             'UAT3'], 
            //             description: 'UI Environment', 
            //             name: 'UI_ENV')
            // string(defaultValue: "https://confluence.anthem.com/display/MAAA/WSR+-+Dead+Pool", description: 'WSR URL', name: 'WSR_URL')                          
            // choice(choices: ['contents-commercial-rest-war', 
            //             'contents-commercial-rest-war', 
            //             'ma-authentication-war', 
            //             'ma-cm-war'], 
            //             description: 'War Files', 
            //             name: 'WAR_FILES')
            // string(defaultValue: '8.0.308', description: 'IHS Version', name: 'IHS_VERSION')
            string(defaultValue: 'YOUR_USER_ID', description: 'Artifictory User ID', name: 'MY_USERID')
            //password(defaultValue: '', description: 'Artifactory Password', name: 'MY_PASSWORD')
//             text(name: 'MY_FILE_LIST', 
//                 defaultValue: '''https://artifactory.anthem.com/artifactory/maven-releases/com/anthem/madt/ui/${UI_ENV}/${IHS_VERSION}/ABC-${IHS_VERSION}.tar.gz
// https://artifactory.anthem.com/artifactory/maven-releases/com/anthem/madt/ui/${UI_ENV}/${IHS_VERSION}/EBCBS-${IHS_VERSION}.tar.gz
// https://artifactory.anthem.com/artifactory/maven-releases/com/anthem/madt/ui/${UI_ENV}/${IHS_VERSION}/ABCBS-${IHS_VERSION}.tar.gz''', 
//                 description: 'List all linked Artifacts - EXAMPLE - https://artifactory.anthem.com/artifactory/maven-releases/com/anthem/madt/commercial/contents-commercial-rest-war/1.0.0/contents-commercial-rest-war-1.0.0.war ')           
    }
    stages {
        //stage('Cleanup Jenkins Job Workspace'){
            //steps {
                //step([$class: 'WsCleanup'])
            //}
        //}       
        stage('Run Ansible Deploy operation'){        
            steps {            
            wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
                    echo 'Validate Access'
                    ansiblePlaybook credentialsId: 'AG19884_PK',
                    installation: 'ansible', 
                        inventory: '/Users/${MY_USERID}/${INV_FILE}',
                    limit: '${INV_GRP}',
                        playbook: '${WORKSPACE}/inventory_artifacts.yml',
                    colorized: true
                }
            }
        }
        stage('Demo Performance'){
            steps {
                echo 'Clap if you liked the demo!'
            }
        }

    }
}
