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
          steps{
           sh """
                docker build -t docker.io/moatazxz/myapp:v1  .
            """
        
          }
      }

    stage ("Push Image")
      {
          steps{
           sh """
                 docker push docker.io/moatazxz/myapp:v1
            """
        
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


