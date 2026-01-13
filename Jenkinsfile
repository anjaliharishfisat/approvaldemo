pipeline{
  agent any
  stages {
    stage ( 'Checkout' ) {
      steps {
        echo 'Pulling code from Github'
        checkout sm 
      }
    }
    stage ( 'Build' ) {
      steps {
        echo 'Building project is going on'
        bat 'echo Build complete successfully!'
        
      }
    }
     stage ( 'Validation check' ) {
      steps {
        echo 'Validating project readiness'
        bat '''
        findstr READY=true check.txt > nul
        if errorlevel 1 (
          echo Validation failed
          exit 1
        ) else (
            echo validation passed
          )
          '''
        
        
      }
    }
    stage ( 'Manager approval' ) {
      steps {
        input message: 'Approve deployment?', ok: 'approve'
      }
    }
    stage ( 'Ready for Deployment' ) {
      steps {
        echo 'Deployment approved and ready'
      }
    }
 }
}
