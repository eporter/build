pipeline {
  agent none
  
  environment {
  	NODE_VER = '8.1.0'
  }

  post {
  	success {
  		
  	}
  }

  stages {
    stage('Beginning') { agent any
    	environment {
    		NEW_VAR = 'Howdy'
    	}
      steps {
        echo 'Hello world'
        sh 'echo $NODE_VER'
        echo "${env.NEW_VAR}"
      }
    }

    stage('Who Am I?') { agent any
    	environment {
    		DEPLOY_VERSION = 'prod'
    	}
    	steps {
    		echo "${env.NEW_VAR}"
    		sh 'host -t TXT pgp.michaelhholley.us |awk -F \'"\' \'{print $2}\''
    	}
    }

    stage('Deploy to stage?') {agent none
    	step {
    		input 'Deploy to stage?'
    	}
    }
  }
}
