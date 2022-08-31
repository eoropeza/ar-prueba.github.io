pipeline {
    agent none
    stages {
        stage('Clean'){
            agent any
            steps {
                script {
                    try{
                    sh "docker stop nginx-test"
                    sh "docker rm nginx-test"
                    echo "success clean"
                    }catch(e){
                        echo "success clean"
                    }
                }
            }
        }
        
        stage('Publish'){
            agent any
            steps {
                script {
                    def dockerfile = 'Dockerfile'
                    def customImage = docker.build("nginx-test",
                                       "-f ${dockerfile} .")
                    customImage.withRun("-d -p 8090:80 --name nginx-test nginx-testing"){
                        sh 'ls -la'
                    }
                   customImage.run("-d -p 8090:80 --name nginx-test")
                }
            }
        }

    }
}
