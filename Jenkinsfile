pipeline{
    agent any
    parameters{
        string(name: 'ubuntu_slave' , defaultValue: '18.220.76.185' , description: 'ubuntu_tomcat')
    }
    stages{
        stage("Building War File"){
            steps{
                echo "Building the war file"
                sh "mvn clean install"
            }
            post{
                success{
                    echo "Build Successfull Harish"
                    archiveArtifacts artifacts: '**/target/*.war'
                    }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Copying War to ubuntu Slave"){
            steps{
                echo "Deploying War file"
                sh "scp -i /home/ubuntu/Aadithya.pem **/target/*.war ubuntu@${params.ubuntu_slave}:/home/ubuntu/apache-tomcat-8.5.45/webapps"

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