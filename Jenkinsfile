pipeline {
    agent any
    tools {
        maven "maven-3.8.4"
    }
    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/vytec-casemgt/core-app.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean deploy -s settings.xml"
            }

            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
        stage('deploy') {
            steps {
               
                sh 'echo "started deployment on dev"'
            }

           
        }
    }
}
