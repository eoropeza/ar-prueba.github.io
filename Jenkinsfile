pipeline {
    agent none
    stages {
        stage('Publish'){
            agent any
            steps {
                script {
                    def dockerfile = 'Dockerfile'
                    sh "docker stop nginx-test"
                    sh "docker rm nginx-test"
                    def customImage = docker.build("nginx-test",
                                       "-f ${dockerfile} .")
                   customImage.run("-d -p 8090:80 --name nginx-test")
                }
            }
        }

    }
}
