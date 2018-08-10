pipeline {
	
     agent {
        node {
            label 'docker'
        }
    }
	tools { 
        maven 'MAVEN'  
    }
   stages { 	
        stage('Build Jar') {
            steps {
                sh 'sudo apt-get install -y docker.io'
            }
        }
        stage('Build Image') {
            steps {
                script {
                	app = docker.build("iamsethi786/docker-selenium")
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
			        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
			        	app.push("${BUILD_NUMBER}")
			            app.push("latest")
			        }
                }
            }
        }        
    }
} 
