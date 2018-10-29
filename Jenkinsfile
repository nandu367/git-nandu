pipeline {
    agent any 
    stages {
        stage('Compilation and Artifact Creation') {
		steps{
			sh '''
				cd hilton-admin-gw
				mv scripts DeployAdmin
				tar -cf DeployAdmin-${BUILD_NUMBER}.tar -C DeployAdmin .
			'''
		}
	}
	stage('Copy Artifact in Dev Environment') {
		steps{
			sh '''
				pwd
				scp hilton-admin-gw/DeployAdmin-${BUILD_NUMBER}.tar 
			'''
		}
	}
        stage('Parallel Stage') {
            parallel {
                stage('Dev Deployment') {
		steps{
			sh '''
				echo ${BRANCH_NAME}
				if [[ "${BRANCH_NAME}" == *release*DG || "${BRANCH_NAME}" == *hotfix* ]] || [[ "${BRANCH_NAME}" == *develop* ]]
				then
					mkdir -p /appsnfs/DeployAdmin-${BUILD_NUMBER}
					gtar -C /appsnfs/DeployAdmin-${BUILD_NUMBER}/ -xvf /appsnfs/DeployAdmin-${BUILD_NUMBER}.tar
					chmod -R 755 /appsnfs/DeployAdmin-${BUILD_NUMBER}
					unlink /appsnfs/DeployAdmin
					ln -sf /appsnfs/DeployAdmin-${BUILD_NUMBER} /appsnfs/DeployAdmin
				fi
				exit 0
				EOF
			'''
		}
	}
        stage('Copy Artifact in QA Environment') {
                steps{
                        sh '''
                                pwd
                                scp hilton-admin-gw/DeployAdmin-${BUILD_NUMBER}.tar 
                        '''
                }
        }
        stage('QA Deployment') {
		steps{
			sh '''
                                echo ${BRANCH_NAME}
                                if [[ "${BRANCH_NAME}" == *release*DG || "${BRANCH_NAME}" == *hotfix* ]] || [[ "${BRANCH_NAME}" == *develop* ]]
                                then
					mkdir -p /appsnfs/DeployAdmin-${BUILD_NUMBER}
					gtar -C /appsnfs/DeployAdmin-${BUILD_NUMBER}/ -xvf /appsnfs/DeployAdmin-${BUILD_NUMBER}.tar
					chmod -R 755 /appsnfs/DeployAdmin-${BUILD_NUMBER}
					unlink /appsnfs/DeployAdmin
					ln -sf /appsnfs/DeployAdmin-${BUILD_NUMBER} /appsnfs/DeployAdmin
				fi
				exit 0
				EOF
			'''
		}
	}
        stage('Copy Artifact in Staging Environment') {
                steps{
                        sh '''
                                pwd
                                scp hilton-admin-gw/DeployAdmin-${BUILD_NUMBER}.tar 
                        '''
                }
        }
	stage('Staging Deployment') {
		steps{
			sh '''
                                echo ${BRANCH_NAME}
                                if [[ "${BRANCH_NAME}" == *release*DG || "${BRANCH_NAME}" == *hotfix* ]] || [[ "${BRANCH_NAME}" == *develop* ]]
                                then
					mkdir -p /appsnfs/DeployAdmin-${BUILD_NUMBER}
					gtar -C /appsnfs/DeployAdmin-${BUILD_NUMBER}/ -xvf /appsnfs/DeployAdmin-${BUILD_NUMBER}.tar
					chmod -R 755 /appsnfs/DeployAdmin-${BUILD_NUMBER}
					unlink /appsnfs/DeployAdmin
					ln -sf /appsnfs/DeployAdmin-${BUILD_NUMBER} /appsnfs/DeployAdmin
				fi
				exit 0
				EOF
			'''
		}
	}
            }
        }
    }
}
