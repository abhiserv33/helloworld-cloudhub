pipeline {
	agent any
	
	stages {
		stage('Build') {
			steps {
				git url: 'https://github.com/abhiserv33/helloworld-cloudhub.git', branch: 'master', credentialsId: '23c36c5f-e294-4923-8190-873c62acbe17'
				bat "mvn -Dmaven.test.failure.ignore=true clean package"
			}
		}
		
		stage('Deploy') {
			steps {
				git url: 'https://github.com/abhiserv33/helloworld-cloudhub.git', branch: 'master', credentialsId: '23c36c5f-e294-4923-8190-873c62acbe17'
				bat "mvn -Dmaven.test.failure.ignore=true clean install deploy -DmuleDeploy"
			}
		}
		
		stage('Test') {
			steps {
				git url: 'https://github.com/abhiserv33/helloworld-cloudhub.git', branch: 'master', credentialsId: '23c36c5f-e294-4923-8190-873c62acbe17'
				bat "newman run https://www.getpostman.com/collections/b122c7c57be11651821a -r htmlextra"
			}
		}
	}
	
	post {
		success {
			mail bcc: '', body: "Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL of build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "Build SUCCESS: ${env.JOB_NAME}", to: "abhinav.sarkar@apisero.com";
    		}
		
        	failure {
			mail bcc: '', body: "Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL of build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "FAILURE: ${env.JOB_NAME}", to: "abhinav.sarkar@apisero.com";
    		}
	}
}
