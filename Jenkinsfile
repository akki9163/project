pipeline {
    agent any
	
	environment{ 
		dockerImage=''
		registry='akki9163/nodeapp1'
		registryCredential='akki-dchub'
	}
	
   stages{
		stage('git_clone'){
			steps{
				git 'https://github.com/akki9163/demo.git'
				}
				}
		stage('build docker image'){
			steps{
				script{
					dockerImage=docker.build registry
				}
			}
		}
		stage('docker hub upload'){
			steps{
				script{
					docker.withRegistry('', registryCredential){
					dockerImage.push()
				}
				}
			}
		}
	}
}
