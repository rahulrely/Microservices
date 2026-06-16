pipeline {
    agent any

    stages {

        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig(
                    caCertificate: '',
                    clusterName: 'AKS-1',
                    contextName: '',
                    credentialsId: 'k8-tokn',
                    namespace: 'webapps',
                    restrictKubeConfigAccess: false,
                    serverUrl: 'https://aks-1-microservicesfin-9ab869-umma1mj2.hcp.centralindia.azmk8s.io'
                ) {
                    sh 'kubectl apply -f deployment-service.yml'
                    sleep(time: 60, unit: 'SECONDS')
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withKubeConfig(
                    caCertificate: '',
                    clusterName: 'AKS-1',
                    contextName: '',
                    credentialsId: 'k8-tokn',
                    namespace: 'webapps',
                    restrictKubeConfigAccess: false,
                    serverUrl: 'https://aks-1-microservicesfin-9ab869-umma1mj2.hcp.centralindia.azmk8s.io'
                ) {
                    sh 'kubectl get all -n webapps'
                }
            }
        }
    }
}