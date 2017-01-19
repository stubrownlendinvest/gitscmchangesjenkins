

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
                
				slackSend channel: '#jenkinscitests', color: '#439FE0', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
               
            }
        }
        stage('Build & Tests'){
            steps {
            sh "echo in another stage"
                
            }
        }
    }
  post {
      // always, unstable, aborted, failure, success, changed
    success {
    	slackSend channel: '#jenkinscitests', color: '#439FE0', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
       
    }
    failure {
        slackSend channel: "#jenkinscitests", message: "Failed to build : ${BRANCH_NAME}"
        
    }
    always {
    	slackSend channel: "#jenkinscitests", message: "Allways to build : ${BRANCH_NAME}"
    
    }
    
    
  }
}
