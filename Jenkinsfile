node {
    def app
    environment { DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-oza') }

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("getintodevops/example-app")
    }
    
    stage('login to docker hub') {
        steps {
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        }
        
    }

    stage('Push image') {
        /* Finally, we'll push the image into Docker Hub */
        steps {
            sh 'docker push wizebird/kloud45:latest'
        }

    }
}
