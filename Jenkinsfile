ipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {

        stage('Build') { 
            steps { 
//                 sh 's docker build -t omarkorety/node-app-test:$BUILD_TAG .' 
                sh "ls "
                 sh ' docker build -t omarkorety/node-app-test:$BUILD_TAG .'
            }
            post {
                success {
                    slackSend color: "good", message: "slack message is done "

                }

            }
        }
    }
}

      

//         stage('docker_slave'){
//             steps {
//                 withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                
//                 sh ' docker login -u ${USERNAME} -p ${PASSWORD}'
//                 sh ' docker push omarkorety/node-app-test:$BUILD_TAG'
//                 }
                  

//             }
//         }

//     }
//  }
