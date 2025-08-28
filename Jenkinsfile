pipeline {
    agent {
	docker{
		image 'postman/newman:latest'
		args '--entrypoint='
	       }
    }
    environment {
        COLLECTIONS_PATH = 'collections/'
    }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install -g newman'
            }
        }

        stage('Run API Tests') {
            steps {
                   sh './batchs/home.sh'
	           sh './batchs/welcome.sh'
            }
        }
    }

    post {
        always {
            junit 'results/newman-report.xml'
        }
    }
}
