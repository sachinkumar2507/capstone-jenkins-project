pipeline {
    agent{
            label "slave3"
        }
        tools {
            maven 'maven'
            jdk 'jdk 8'
        }
    stages {
               stage("clean-up"){
            steps{
                sh "mvn clean"
            }
        }

        stage('Testing') {
            steps {
                echo 'Testing the application...'
                sh "mvn clean test"
            }
        }
    }
    post {
        success{
        echo "Testing stage successful"
        }
        failure{
        echo "Testing stage failed"
        }
    }
}
