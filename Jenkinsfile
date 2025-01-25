pipeline {
    agent any

 // stages {
 //    stage('Checkout git repo') {
 //        steps {
 //                credentialsId: 'arbaazgit',
 //                url: 'https://github.com/shaikharbaaz101/jenkins_t.git'

 //            sh "ls -lat"
 //        }
 //    }
    
    stage('build image') {
        steps {
            echo "hi from muli-dev branch"
        }
    }
    stage('build image') {
        steps {
            sh "docker build -t nginxjenkins:${params.DOCKER_TAG} ."
        }
    }
    stage('stop existing image') {
        steps {
            sh """
                    docker ps -q | xargs -r docker stop
            """
        }
    }


    stage('run image') {
        steps {
            sh "docker run -d -p 8082:80 nginxjenkins:${params.DOCKER_TAG}"
        }
    }
}
}
