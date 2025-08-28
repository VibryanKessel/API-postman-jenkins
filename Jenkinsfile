pipeline {
    agent {
	docker{
		image 'postman/newman:latest'
		args '--entrypoint='
	       }
    }
    triggers {
        upstream 'Selenium-CICD'
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
