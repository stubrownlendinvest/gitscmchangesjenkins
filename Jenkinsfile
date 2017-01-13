currentBuild.displayName = "#" + currentBuild.number + " - " + env.BRANCH_NAME

if (env.BRANCH_NAME == "master") {
    env.ENV_SUFFIX = ""
} else {
    env.ENV_SUFFIX = ".qa"
}



    agent any

    stages {
        stage('Build'){
            steps {
               sh "ls -lart"
            }
        }
        stage('More Stuff'){
            steps {
                sh 'echo not doing much'
                
            }
        }
        stage('Tests') {
            steps {
                sh "ls -lart"
        }
    }
  }
  post {
      // always, unstable, aborted, failure, success, changed
    success {
        sh "echo was a success"
    }
    unstable {
        echo 'UNSTABLE'
    }
    failure {
        echo 'FAILED'
        
    }
    always {
        // notify slack
        slackSend channel: "#jenkinscitests", message: "Successfully built : ${DOCKER_IMAGE}"
        
    }
  }

