# ci/cd

pipeline {
    agent any
      environment {
        K8S_CLUSTER_ID = 'jpe1-caas1-dev1'
        K8S_NAMESPACE = "${env.JOB_NAME.split('/')[3]}"
    }
    stages {
        stage('scm') {
            steps {
                git branch: 'main', url: 'https://github.com/ArnabMajumder009/CaasRepo.git'
            }
        }
        
         stage('k8s') {
            steps {
                
                script{
                   // Apply deployment
                   cpd.kubectl('apply -f app-deployment.yaml')
                   cpd.kubectl('apply -f db-deployment.yaml')
                   cpd.kubectl('apply -f mysql-configMap.yaml')
                   cpd.kubectl('apply -f mysql-secrets.yaml')
                    
                   
               }
                
            }
        }
        
        
    }
}
