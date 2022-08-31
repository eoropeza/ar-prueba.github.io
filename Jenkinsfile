pipeline {
    agent none
    stages {
        stage('Publish'){
            agent any
            steps {
                script {
                    def dockerfile = 'Dockerfile'
                    def customImage = docker.build("nginx-test",
                                       "-f ${dockerfile} .")
                   customImage.run("-d -p 8090:80 nginx-test")
                }
            }
        }

    }
}
