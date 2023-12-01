pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            steps {
                // Checkout code from SCM (e.g., Git)
                git url: 'https://github.com/GABIMARU22/Bipolar_Assignment'
            }
        }

        stage('Testing with JUnit') {
            steps {
                // Run tests using JUnit
                sh 'mvn test'
            }
        }

        stage('Build with Maven') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }

        stage('Dockerize Application') {
            steps {
                // Build Docker image
                sh 'docker build -t helloworld .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                // Push Docker image to DockerHub
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker push your-docker-image'
                }
            }
        }

        stage('Deploy to Kubernetes Cluster') {
            steps {
                // Deploy to Kubernetes cluster using kubectl
                withCredentials([string(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
                    sh 'echo "$KUBECONFIG" > deployment.yaml'
                    sh 'kubectl apply -f deployment.yaml'
                }
            }
        }
    }
}
