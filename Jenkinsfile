pipeline {
    agent any

    stages {
        stage('Stage 1 - Basic Setup') {
            steps {
                sh '''
                    # Install Docker only if not available
                    if ! command -v docker >/dev/null 2>&1; then
                        echo "Docker not found. Installing Docker..."
                        apt update -y
                        apt install -y docker.io
                    else
                        echo "Docker is already installed: $(docker --version)"
                    fi

                    # Install Docker Compose only if not available
                    if ! command -v docker-compose >/dev/null 2>&1; then
                        echo "Docker Compose not found. Installing Docker Compose..."
                        apt update -y
                        apt install -y docker-compose
                    else
                        echo "Docker Compose is already installed: $(docker-compose --version)"
                    fi
		    sudo service docker start
                '''
            }
        }
	stage("Stage 2 - Building Docker Image"){
		steps{
			sh 'echo Hello';
			sh "echo Hi";
			sh '''echo How are you''';
			sh "sudo docker image build -t oklabsin/myimage:t${BUILD_NUMBER} -f Dockerfile.app ."
		}

	}
    }

}
