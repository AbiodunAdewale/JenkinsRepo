pipeline {
	agent any 
		stages{
			stage('1-clone'){
				steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/LateefAdewale/JenkinsRepo.git']]])
				git branch: 'main', credentialsId: 'github-id', url: 'https://github.com/LateefAdewale/JenkinsRepo.git'
				}
			}
			stage('2-uptime-lateef'){
				steps{
					sh 'bash -x /var/lib/jenkins/workspace/team3-hook-pipeline/lateef.sh'
				}
			}
		}
}
