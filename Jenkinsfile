/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
]

def branchName = env.BRANCH_NAME.toLowerCase()
def stageName = env.STAGE

switch (branchName) {	
	case 'production':
		stageName = 'production'
		projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
		break
	case 'master':
		stageName = 'staging'
		projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
		break
	case 'develop':
		stageName = stageName ? stageName : 'development'
		projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
		break
}

properties(projectProperties)

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + branchName
		sh 'echo ' + stageName
		sh 'echo ' + env.CHANGE_ID
    }
}