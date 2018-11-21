properties([pipelineTriggers([pollSCM('H/10 * * * *')])])

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + env.BRANCH_NAME
    }
}