pipeline{
    agent any
        stages
{
    stage('Build Docker Image'){
        steps{
            echo "Build Docker Image"
            bat "docker build  -t kubedemoapp:v1 ."
        }
    }
    stage('Docker Login'){
        steps{
            bat 'docker login -u saradasrinija -p  22251A1234'
        }
    }
    stage('push Docker Image to Docker Hub'){
        steps{
            echo "push Docker Image to  Docker Hub"
            bat "docker tag kubedemoapp:v1 saradasrinija/sample:kubdeimage1"

            bat "docker push saradasrinija/sample:kubeimage1"
        }
    }
    stage('Deploy to  kubernetes'){
        steps{
            bat 'kubectl  apply -f  deployment.yaml --validate'
            bat 'kubectl apply -f service.yaml'
        }
    }
}
}