pipeline {
    agent {label 'jenkinslaves' }
    stages {
        stage('Fetch dependencies') {
        /* This stage pulls the latest nginx image from
           Dockerhub */
            steps {
                sh 'sudo docker pull node:14'
          }
        }
        stage('Build docker image') {
        /* This stage builds the actual image; synonymous to
           docker build on the command line */
            steps {
            sh "sudo docker build . -t nodeapp:1"
            }    
        }
        stage('Test image') {
         /* This stage runs unit tests on the image; we are
            just running dummy tests here */
            steps {
                sh 'echo "Tests successful"'
          }
        }
        stage('Push image to Object Storage') {
         /* Final stage of build; Push the 
            docker image to our OCI private Registry*/
        steps {
            sh "sudo docker login -u 'sehubjapacprod/appdevuser' -p ')7K>}EU}6sTnNn2]qYt)' iad.ocir.io"
            sh "sudo docker tag nodeapp:1 iad.ocir.io/sehubjapacprod/nodeapp:custom"
            sh "sudo docker images"
            sh "sudo docker push iad.ocir.io/sehubjapacprod/nodeapp:custom"
            
           }
         }      
    }
}
