pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker image build -t 35.187.184.199:5000/testje/nginx:latest .'
                sh 'docker push 35.187.184.199:5000/testje/nginx:latest'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'export KUBECONFIG=/home/niel/kubeconfig'
                sh 'oc apply -f deployment.yaml'
            }
        }
        stage('Test') {
            steps {
                sh 'export KUBECONFIG=/home/niel/kubeconfig'
                sh 'sleep 5'
                sh 'oc get pods'
                sh 'oc get deploy'
                sh 'oc get pvc'
                sh 'oc get pv'
            }
        }
    }
}

