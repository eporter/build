pipeline {
  agent none
  
  environment {
  	NODE_VER = '8.1.0'
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
    		DEPLOY_VERSION = 'stage'
    	}
    	steps {
    		echo "${env.NEW_VAR}"
    		sh 'host -t TXT pgp.michaelhholley.us |awk -F \'"\' \'{print $2}\''
    	}
    }

    stage('Deploy to stage?') {agent none
    	steps {
    		input 'Deploy to stage?'
    	}
    }
  }
}
