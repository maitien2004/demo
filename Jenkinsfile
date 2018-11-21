properties([pipelineTriggers([pollSCM('H/5 * * * *')])])

node {
	stage('Demo'){
		def str = 'OK'
		sh 'echo ' + str.toLowerCase()
        sh 'echo develop'
		sh 'echo ' + env.BRANCH_NAME + ' hello'
    }
}