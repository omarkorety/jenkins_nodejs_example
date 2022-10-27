pipeline { 
    agent {label "docker_slave"} 
    options {
        skipStagesAfterUnstable()
    }
    stages {

        stage('Build') { 
            steps { 
                sh 'sudo docker build -t omarkorety/node-app-test:$BUILD_TAG .' 
            }
        }

        stage('ec2_slave'){
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                
                sh 'sudo docker login -u ${USERNAME} -p ${PASSWORD}'
                sh 'sudo docker push omarkorety/node-app-test:$BUILD_TAG'
                }
                  

            }
        }

    }
}
