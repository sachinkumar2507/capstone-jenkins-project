pipeline {
    agent {
        label 'master'
    }
    stages {
        stage("clean-up"){
            steps{
                sh "mvn clean"
            }
        }
	           stage("test"){
            steps{
                sh "mvn test"
            }
        }
	           stage("package"){
            steps{
                sh "mvn package"
            }
        }
    }
    post {
         success {
            echo "Packaging successful"
        }
        failure {
            echo "Packaging unsuccessful"
        }
    }
}
