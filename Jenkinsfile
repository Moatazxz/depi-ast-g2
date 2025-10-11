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

    stage ("build2")
      {
          steps{
           sh """
                 echo "build docker Image"
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


