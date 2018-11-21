/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
	pipelineTriggers([pollSCM('H/15 * * * *')])
]

properties(projectProperties)

def stageName

if(env.BRANCH_NAME == null) {
	stageName = env.STAGE
} else {
	switch (env.BRANCH_NAME.toLowerCase()) {	
		case 'production':
			stageName = 'production'
			break
		case 'master':
			stageName = 'staging'
			break
		case 'develop':
			stageName = env.STAGE ? env.STAGE : 'development'
			break
	}
}

if(!stageName) {
	node {
		stage('Error'){
			echo 'stage is not defined'
		}
	}
} else {
	node {
		stage('Demo'){
			sh 'echo master'
			sh 'echo ' + env.BRANCH_NAME
			sh 'echo ' + stageName
		}
	}
}