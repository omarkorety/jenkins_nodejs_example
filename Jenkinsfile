pipeline { 
    agent {label "slave1"} 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                git 'https://github.com/mahmoud254/jenkins_nodejs_example.git' 
            }
        }
        stage('Test'){
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                
                sh 'docker login -u ${USERNAME} -p ${PASSWORD}'
                sh 'docker push omarkorety/node-app-test:$BUILD_TAG'
                  

            }
        }

    }
}
