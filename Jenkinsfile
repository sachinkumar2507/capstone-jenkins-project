pipeline{
    agent{
        label "slave1"
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
           mail to: 'sachin.kumar@knoldus.com',
			subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
       }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
