pipeline{
        agent {
            label 'master'
        }
        tools {
            maven 'maven_home'
            jdk 'java_home'
        }
    
    stages{
        
        stage ('Code Compile') {
            steps{
                sh """
                mvn compile
                """
            }
        }
            
        stage ('Packaging') {
            steps {
                sh """
                mvn package
                """
            }
        }
            
        stage ('Build Docker Image') {
            steps {
                sh """
                docker build -t archieismael/my-app:1.0 .
                """
            }
        }

        stage ('Build Docker Image') {
            steps {
                    withCredentials([string(credentialsId: 'docker-hub-pass', variable: 'docker-hub-pass')]) {
                       sh """
                       docker login -u archieismael -p ${dockerHubPwd}
                       """
                    }
                sh """
                    docker push archieismael/my-app:1.0
                """
            }
        }
 
   }

}
