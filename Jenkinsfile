/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
]

def branch = env.BRANCH_NAME.toLowerCase()
def stage = env.STAGE

switch (branch) {	
	case 'production':
		stage = 'production'
		projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
		break;
	case 'master':
		stage = 'staging'
		projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
		break;
	case 'develop':
		stage = 'development'
		projectProperties.add(pipelineTriggers([pollSCM('H/15 * * * *')]))
		break;
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