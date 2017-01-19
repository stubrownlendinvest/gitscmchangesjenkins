

currentBuild.displayName = "#" + currentBuild.number + " - " + env.BRANCH_NAME

if (env.BRANCH_NAME == "master") {
    env.ENV_SUFFIX = ""
} else {
    env.ENV_SUFFIX = ".qa"
}


pipeline {
    
    agent any 
	
    stages {
        stage('Setup environment'){
            steps {
                
				//slackSend channel: '#jenkinscitests', color: '#439FE0', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}] (${env.BUILD_URL})'"
               
               sh "sleep 3"
               sh "echo in steps 1"
            }
        }
        stage('Build & Tests'){
            steps {
            sh "echo in another step"
            sh "ls -lart"
            sh "sleep 5"
                
            }
        }
    }
  post {
      // always, unstable, aborted, failure, success, changed
    success {
    	slackSend channel: '#jenkinscitests', color: '#43e062', message: "Successfully built: '${env.JOB_NAME} [${env.BUILD_NUMBER}]' 'stuart ' (${env.BUILD_URL}) "
       
    }
    failure {
        slackSend channel: '#jenkinscitests', color: '#e04343', message: "Failed to build: '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
        slackSend channel: '#ci_failed_builds', color: '#e04343', message: "Failed to build: '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
       
        
        
    }
    always {
    	//slackSend channel: "#jenkinscitests", message: "Allways to build : ${env.BRANCH_NAME}"
    	slackSend channel: '#jenkinscitests', color: '#439FE0', message: "Build Started: '${env.JOB_NAME} [${env.BUILD_NUMBER}] (${env.BUILD_URL})'"
    	sh "echo hello"
    }
    
    
  }
}
