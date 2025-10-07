pipeline {
 agent any

 tools {
   nodejs 'node24'
 }
stages {

    stage ("build")
      {
          steps{
           sh """
                 npm -v
            """
        
          }
      }

    stage ("test")
      {
          steps{
           sh """
                 echo "Test Code"
            """
        
          }
      }

    stage ("build docker")
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
