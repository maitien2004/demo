/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
]

def Branch = env.BRANCH_NAME
def Stage = env.STAGE


properties(projectProperties)

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + Branch
		sh 'echo ' + Stage
		sh 'echo ' + env.CHANGE_ID
    }
}