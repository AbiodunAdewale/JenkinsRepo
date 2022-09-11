pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHub Id', url: 'https://github.com/LateefAdewale/JenkinsRepo.git']]])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
    stage('unittest'){
        steps{
            sh 'mvn test'
        }
    }
    stage('codequality'){
        steps{
      mvn 'clean verify sonar:sonar \
  -Dsonar.projectKey=Lateef-pipeline \
  -Dsonar.host.url=http://ec2-18-222-28-94.us-east-2.compute.amazonaws.com:9000 \
  -Dsonar.login=sqp_bfbfd2cc78b37d85ca8f5b7ebd9dde76218c27db'
        }
    }
  }
}
