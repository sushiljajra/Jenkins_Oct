pipeline{
  agent any
  parameters{
     string(name: 'FIRST_NAME', defaultValue: 'ANIL')
     string(name: 'LAST_NAME', defaultValue: 'DOLLOR')
  }
  stages{
    stage(''' Docker Installation '''){
      steps{
        sh  '''
          apt update -y
          apt upgrade -y
          apt install sudo docker.io docker-compose -y
          sudo service docker start
          sudo service docker status
        '''
      }
    }
    stage("Stage 1"){
      steps{
        //sh 'linux command';
        sh "echo Hello ${FIRST_NAME} ${LAST_NAME}"
        sh ''' 
            whoami 
            ls -al
            cat /etc/os-release
        '''
      }
    }
    stage("PULL THE IMAGE"){
      steps{
        sh 'sudo docker image pull ubuntu:latest'
      }
    }
  }
  post{
    cleanup{
       echo "Performing cleanup..."
      
    }
  }
}
