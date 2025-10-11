pipeline {
 agent any

 // tools {
 //   nodejs 'node24'
 // }

 environment {
  myrepo= "docker.io/moatazxz"
  appname= "myapp"
  env= "test"
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
        when {
         // anyof{
         //  branch 'main'
         //  environment name: 'env', value: 'test'
         // }

           allof{
          branch 'main'
          environment name: 'env', value: 'test'
         }
        }
           
          steps {
           sh """
                
                docker build -t ${myrepo}/${appname}:${env.BUILD_NUMBER}  .
      
            """
        
          }
      }
      

    stage ("Push Image")
      {

           when {
           environment name: 'env', value: 'test'
        }
           
          steps{
           withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]){
           sh """
                 docker login -u $DOCKER_USER  -p $DOCKER_PASS
                 docker push ${myrepo}/${appname}:${env.BUILD_NUMBER}
            """
        
          }
      }
      }

    stage ("Deploy")
      {

       when {
          branch 'prod'        
       }
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


