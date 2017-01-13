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
                slackSend channel: "#jenkinscitests", message: "Build Started: ${env.JOB_NAME} ${env.BRANCH_NAME}"

               
            }
        }
        stage('Build & Tests'){
            steps {
                
            }
        }
    }
  post {
      // always, unstable, aborted, failure, success, changed
    success {
        
    }
    failure {
        slackSend channel: "#jenkinscitests", message: "Failed to build : ${BRANCH_NAME}"
        
    }
    always {
        
    }
  }
}
