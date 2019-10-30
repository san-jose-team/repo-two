pipeline {
    //agent {label 'Test-QA' }
	agent any
	environment {
        GIT_CREDS = credentials('402a62c6-3d70-4d77-b092-816438a14ff5')
    }
    stages {
        stage('Example Build') {
            steps {
				checkout scm
                sh '''
					echo ${GIT_CREDS_USR} ${GIT_CREDS_PSW} > .testcreds
					cat .testcreds
					cat /etc/os-release
					echo Hello world
					ls -la
				'''
				script {
					timeout(time: 4, unit: 'HOURS') {
                        input message: 'Approve EXIT?'
                    }
				}
            }
        }
    }
}

