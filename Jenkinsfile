/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
	pipelineTriggers([pollSCM('H/15 * * * *')])
]

properties(projectProperties)

def stage

if(env.BRANCH_NAME == null) {
	stage = env.STAGE
} else {
	switch (env.BRANCH_NAME) {	
		case 'production':
			stage = 'production'
			break
		case 'master':
			stage = 'staging'
			break
		case 'develop':
			stage = env.STAGE ? env.STAGE : 'development'
			break
	}
}

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + env.BRANCH_NAME
		sh 'echo ' + stage
    }
}