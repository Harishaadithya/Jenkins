pipeline{
    agent any
    stages{
        stage("Building War File"){
            steps{
                echo "Building the war file"
                sh "mvn clean install"
            }
            post{
                success{
                    echo "Archive Artifatcs"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Deploying to Tomcat WebApplication Server"){
            steps{
                echo "Deploying War file"
                sh "sudo cp **/target/*.war /home/ubuntu/apache-tomcat-8.5.45/webapps"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}