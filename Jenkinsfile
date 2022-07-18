pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           // The below will clone your repo and will be checked out to master branch by default.
           //git credentialsId: 'jeevas008', url: 'https://github.com/jeevas008/Jenkins.git'
           git branch: 'main', url: 'https://github.com/jeevas008/Jenkins.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // List all branches in your repo. 
           sh "git branch -a"
           // Checkout to a specific branch in your repo.
           sh "main"
          }
       }
    }
  }
}
