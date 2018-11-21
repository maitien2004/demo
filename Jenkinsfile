properties([pipelineTriggers([pollSCM('H/5 * * * *')])])

node {
	stage('Demo'){
        sh 'echo develop'
		sh 'echo ' + env.BRANCH_NAME + ' hello'
    }
}