pipeline{
        agent {
            label 'master'
        }
        tools {
            maven 'maven_home'
            jdk 'java_home'
        }
    
    stages{
        
        stage ('Packaging') {
            steps {
                sh """
                mvn package
                """

            }
        }

   }

}
