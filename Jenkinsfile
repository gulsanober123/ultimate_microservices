pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'Vikash-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://7BF79E786B2FBB5582998BF71E1290D6.gr7.us-west-2.eks.amazonaws.com') {
    
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'Vikash-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://7BF79E786B2FBB5582998BF71E1290D6.gr7.us-west-2.eks.amazonaws.com') {
    
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
