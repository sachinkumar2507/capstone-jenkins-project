pipeline{
    agent{
        label "slave"
    }
    tools { 
        maven 'maven' 
        jdk 'jdk 8'
    }
    stages{
        stage("clean-up"){
            steps{
                sh "mvn clean"
            }
        }
	           stage("compile"){
            steps{
                sh "mvn compile"
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
    post{
       always{
	       emailext body: '''$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:
Check console output at $BUILD_URL to view the results.''', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: 'sachinkmr290@gmail.com'
       }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
