pipeline {
agent any
environment
  {
    VERSION = 'latest'

    PROJECT = 'jenkins'

    IMAGE = "$PROJECT"

    ECRURL = 'https://387232581030.dkr.ecr.us-east-1.amazonaws.com/jenkins'

    ECRCRED = 'ecr:us-east-1:jenkins-ecr-credentials'
  }
stages {
 stage('Checkout') {
   steps {
    script {
            git branch: 'main', url: 'https://github.com/jeevas008/Jenkins.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // List all branches in your repo. 
           sh "git branch -a"
           // Checkout to a specific branch in your repo.
           sh "git checkout main"
    }
   }
 }
 //build Build preparations
 stage('Build preparations'){
   steps {
     script {
        echo "build docker images $BUILD_NUMBER"
     }
   }
 }
//Docker build images
stage('Docker build') {
 steps {
    script {
        docker.build("$IMAGE")
    }
 
 }
}
 //docker push images

 stage('Docker push') {
   steps {
    script {
        docker.withRegistry("$ECRURL", "$ECRCRED") 
        {
          docker.image("$IMAGE").push("$VERSION")
        }
    }
   }
 }
}
}

