pipeline{
        agent {
            label 'master'
        }
        tools {
            maven 'maven_home'
            jdk 'java_home'
        }
    
    stages{
    
        stage("SCM Checkout") {
            git 'https://github.com/archieismael/my-app'
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
