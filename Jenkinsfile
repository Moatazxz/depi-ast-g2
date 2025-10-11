pipeline {
 agent any

 // tools {
 //   nodejs 'node24'
 // }

 environment {
  myrepo= "docker.io/moatazxz"
  appname= "myapp"
 }
stages {

    // stage ("build")
    //   {
    //       steps{
    //        sh """
    //              npm -v
    //         """
        
    //       }
    //   }

    stage ("build docker")
      {

           
          steps {
           sh """
                
                docker build -t ${myrepo}/${appname}:${env.BUILD_NUMBER}  .
      
            """
        
          }
      }
      

    stage ("Push Image")
      {
          steps{
           withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]){
           sh """
                 docker login -u $DOCKER_USER  -p $DOCKER_PASS
                 docker push ${myrepo}${appname}:${env.BUILD_NUMBER}
            """
        
          }
      }
      }

    stage ("Deploy")
      {
          steps{
            withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]){
             sshagent(credentials: ['deploy-ssh-key']) {
           sh """
                ssh  -o StrictHostKeyChecking=no  ubuntu@54.211.192.109 '
                   docker ps
                   docker login -u $DOCKER_USER  -p $DOCKER_PASS 
                   docker run -p 80:80 -d ${myrepo}/${appname}:${env.BUILD_NUMBER}
                '
            """
        
          }
      }
      }
      }



}

}



// Variable	Description
// BUILD_NUMBER	Current build number
// BUILD_ID	Unique build ID
// JOB_NAME	Name of the job
// BUILD_URL	URL of the build
// GIT_COMMIT	Git commit hash (if applicable)
// GIT_BRANCH	Git branch name
// WORKSPACE	Job workspace directory


