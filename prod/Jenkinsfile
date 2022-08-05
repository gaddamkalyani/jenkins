pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
				
            }
        }
		stage('Directory') {
            steps {
                sh 'rm -rf test'
				sh 'mkdir test'
            }
        }
		stage('Git checkout') {
            steps {
                git credentialsId: '08cfd5d1-cbd4-42c5-b753-298cb74c7607', url: 'https://github.com/sunil-999/Myrepo.git'
				
            }
        }
		stage('Build') {
            steps {
                sh 'mvn clean package'
				
            }
        }
		stage('Eamil') {
            steps {
                emailext body: '', subject: 'Build status', to: 'devopseekers@gmail.com'
				
            }
        }
    }
}
