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
   }

}
