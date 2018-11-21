properties([pipelineTriggers([cron('H/5 * * * *')])])

node {
	stage('Demo'){
        sh 'echo develop'
		sh 'echo ' + env.BRANCH_NAME
    }
}