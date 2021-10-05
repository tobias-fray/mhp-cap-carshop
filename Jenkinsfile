@Library('piper-lib-os') _

node("ubuntu") {

        stage('Prepare') {
            //deleteDir()
            checkout scm
            setupCommonPipelineEnvironment script: this
        }

        stage('mtaBuild') {
            mtaBuild script: this
            def mtarFilePath = commonPipelineEnvironment.getMtarFilePath()	
            echo mtarFilePath
        }

        stage('Deploy to Dev') {
            cloudFoundryDeploy script: this
        }
}
