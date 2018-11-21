/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
]

def branch = env.BRANCH_NAME
def stage = env.STAGE

if(branch.toLowerCase() == 'production') {
	stage = 'production'
	projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
} else if(branch.toLowerCase() == 'master') {
	stage = 'staging'
	projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
} else {
	stage = stage ? stage : 'development'
	projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
}

properties(projectProperties)

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + branch
		sh 'echo ' + stage
		sh 'echo ' + env.CHANGE_ID
    }
}