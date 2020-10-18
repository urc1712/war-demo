pipeline {
    agent {label 'slave2'}
    
    
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        
        stage ('git-clone') {
            steps {
                git 'https://github.com/urc1712/war-demo.git'
            }
        }
        
        stage ('maven-build')
        {
            steps {
                sh 'mvn clean package'
            }
        }
    
    stage('deploy') {
        steps {
            deploy adapters: [tomcat9(credentialsId: '15123116-d751-4396-8ddb-7f9c4cf5782b', path: '', url: 'http://18.222.78.4:8081/')], contextPath: 'demo-app', onFailure: false, war: '**/*war'
        }
    }
  }
}
