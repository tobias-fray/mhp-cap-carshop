@Library(['piper-lib-os', 'mail-template-lib']) _


node {

try {
    stage('Prepare') {
        deleteDir()
        checkout scm
        setupCommonPipelineEnvironment script: this
    }


    stage('mtaBuild') {
        mtaBuild script: this
    }

    stage('Deploy to DEV') {
        cloudFoundryDeploy script: this
    }
    
    stage('Success') {
        mailTemplate1 script: this
    }

} catch(error) {
    currentBuild.result = 'FAILED'
    mailTemplate1 script: this
    }
}
