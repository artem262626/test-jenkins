pipeline {
    agent any
    
    tools {
        maven "M398"
        jdk 'JDK21'
    }

    stages {
        stage('Echo Version') {
            steps {
                sh 'echo Print Maven Version'
                sh 'mvn -version'
            }
        }
        
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/dasher-org/jenkins-hello-world.git'
                sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('Unit Test') {
            steps {
                script {
                    for (int i = 0; i < 60; i++) {
                        echo "Iteration: ${i}"
                        sleep 1
                    }
                    sh 'mvn test'
                }
            }
        }
    }
}
