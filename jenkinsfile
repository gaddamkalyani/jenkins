pipeline {
    agent any
   tools{
        maven 'MAVEN_HOME' 
    }
     stages {
        stage('gitcheckout') {
            steps {
              git credentialsId: 'b9e6bf1b-e3e2-4161-89b8-102195cc8597', url: 'https://github.com/gaddamkalyani/gitremoteRepo.git'
            }
        }
        stage('Build'){
             steps{
                 sh 'mvn clean package'
             }
        }
        stage('upload'){
             steps{
                nexusArtifactUploader artifacts: [[artifactId: 'hello', classifier: '', file: 'target/hello-1.0.war', type: 'war']], credentialsId: 'aa244d7f-885c-4736-b564-0be0984000e8', groupId: 'com', nexusUrl: '192.168.56.101:9081', nexusVersion: 'nexus3', protocol: 'http', repository: 'mavenpipelinetom', version: '1.0'
        }
             }
             stage('deploy'){
                 steps{
                     deploy adapters: [tomcat9(credentialsId: '22bf56c2-1872-4292-ab69-f56b2b155599', path: '', url: 'http://192.168.56.101:8082/')], contextPath: null, onFailure: false, war: '**/*.war'
                 }
             }
        }
           
    }
