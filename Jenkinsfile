/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '10']],
]

def branch = env.BRANCH_NAME
def stage = env.STAGE


properties(projectProperties)

node {
	stage('Demo'){
        sh 'echo master'
		sh 'echo ' + branch
		sh 'echo ' + stage
		sh 'echo ' + env.CHANGE_ID
    }
}