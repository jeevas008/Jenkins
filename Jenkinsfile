pipeline

    {
    agent any

    environment 

    {

        VERSION = '$BUILD_NUMBER'

        PROJECT = 'nodejs'

        IMAGE = "$PROJECT"

        ECRURL = '387232581030.dkr.ecr.us-east-1.amazonaws.com/jenkins'

        ECRCRED = 'ecr:us-east-1:jenkins-ecr-credentials'

    }

    stages

    {
    stage('cleanup_workdir') 
    
    {

    steps{   
    
    cleanWs()
    
    }
    
    }
    stage('SCM') 
    {

    steps{

    git credentialsId: 'jeevas008', url: 'https://github.com/jeevas008/Jenkins.git'  
    
    }
    
    }

    

     stage('Build preparations')

     {

     steps

     {

     script 

     {

     echo "build docker images"   

     }

     }

     }  

     stage('Docker build')

     {

     steps

     {

     script

     {

    // Build the docker image using a Dockerfile

    docker.build("$IMAGE")

     }

     }

     }

    stage('Docker push')

     {

     steps

     {

     script

     {

     // Push the Docker image to ECR

     docker.withRegistry("$ECRURL", "$ECRCRED") 
      
     {

     docker.image("$IMAGE").push("$VERSION")
     
     }  

     }

     }

     }

     }
    
     }
   
