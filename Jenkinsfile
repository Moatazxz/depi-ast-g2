pipeline {
 agent any

 // tools {
 //   nodejs 'node24'
 // }
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
                
                docker build -t docker.io/moatazxz/myapp:v1  .
            """
        
          }
      }
      

    stage ("Push Image")
      {
          steps{
           withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]){
           sh """
                 docker login -u $DOCKER_USER  -p $DOCKER_PASS
                 docker push docker.io/moatazxz/myapp:v1
            """
        
          }
      }
      }

    stage ("Deploy")
      {
          steps{
           sh """
                 echo "ssh to target server"
            """
        
          }
      }



}

}


