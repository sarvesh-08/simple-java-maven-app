pipeline {
    agent any
    environment{
        DOCKER_IMAGE="sarvesh5011/myapp"
        DOCKER_TAG="latest"
    }
    stages {

        // stage('Build') { 
        //     steps {
        //         sh 'mvn -B -DskipTests clean package'
        //     }
        // }
        stage('checkout code'){
            steps{
                git branch:'master',url:'https://github.com/sarvesh-08/simple-java-maven-app.git'
            }
        }
        stage('Build'){
            steps{
                sh 'podman build -t maven_app .'
            }
        }
        stage('Deploy container'){
            steps{
                sh 'podman -d -p 8081:8081 --name webcontainer maven_app'
            }
        }
    }

}
