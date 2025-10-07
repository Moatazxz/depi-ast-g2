pipeline {
 agent any

stages {

    stage ("build")
      {
          steps{
           sh """
                 echo "Buils node code"
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
