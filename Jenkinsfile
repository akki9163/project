pipeline {
  agent any
  environment{ 
		dockerImage=''
		registry='akki9163/nodeapp2'
		registryCredential='akki-dchub'
	}
  stages {
    stage('git clone') {
      steps {
        git branch: 'main', url: 'https://github.com/akki9163/project.git'
      }
    }
   	stage('building docker image'){
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
