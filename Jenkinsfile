pipeline{
    agent any  
    environment {
        DOCKER_USER     = credentials('jenkins-docker-username')
        DOCKER_PASSWORD = credentials('jenkins-docker-password')
    } 
       stages {
        stage('BuildCode'){
            steps{ 
                sh 'mvn install -DskipTests=true'
            }
        } 
       stage('DockerLogin') {
	  steps{
	    sh 'docker login --username $DOCKER_USER --password $DOCKER_PASSWORD'
		}
	}
       stage('DockerBuild') {
          steps{
            sh 'docker build -t cloudhight/sample:team9 .'
               }
        }
	stage('Push') {

	  steps {
	    sh 'docker push cloudhight/sample:team9'
		}
	}

		}
    }
