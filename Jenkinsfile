/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
	pipelineTriggers([pollSCM('H/15 * * * *')])
]

properties(projectProperties)

def stageName


if(!stageName) return

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + env.BRANCH_NAME
		sh 'echo ' + stageName
    }
}