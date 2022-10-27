pipeline { 
    agent {label "slave1"} 
    options {
        skipStagesAfterUnstable()
    }
    stages {

        stage('Build') { 
            steps { 
                sh 'make' 
            }
        }

        stage('ec2_slave'){
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                
                sh 'docker login -u ${USERNAME} -p ${PASSWORD}'
                sh 'docker push omarkorety/node-app-test:$BUILD_TAG'
                }
                  

            }
        }

    }
}
