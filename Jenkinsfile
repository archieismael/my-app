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

   }

}
