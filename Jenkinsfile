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
	switch (env.BRANCH_NAME) {	
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

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + env.BRANCH_NAME
		sh 'echo ' + stageName
    }
}