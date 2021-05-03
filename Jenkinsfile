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

        stage ('Push Docker Image') {
            steps {
                    //withCredentials([usernameColonPassword(credentialsId: 'archieismael-dockerhub', variable: 'dockerHubPwd')]) {
                    withCredentials([string(credentialsId: 'docker-hub-pass', variable: 'dockerHubPwd')]) {
                       sh """
                       docker login -u archieismael -p ${dockerHubPwd}
                       """
                    }
                sh """
                    docker push archieismael/my-app:1.0
                """
            }
        }

        stage ('Run Docker Container') {
            steps {
                    sshagent(['tomcat-login']) {
                        sh """
                        ssh -o StrictHostKeyChecking=no acasas@10.0.0.50
                        docker run -p 8090:8080 archieismael/my-app:1.0
                        """
                            
                }    
            }
        }
            
   }
   post {
           always {
                sh """
                docker logout
                """
           }     
   }

}
