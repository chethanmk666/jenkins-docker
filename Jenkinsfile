pipeline{
    agent any
   tools {
       maven 'maven'
       jdk 'Java'
   }
    environment {
        dockerhub=credentials('dockerhub')
        
    }
    stages{
        stage('clean')
        {
            steps{
                sh 'mvn clean'
            }
        }

        stage('pack')
        {
            steps{
                sh 'mvn package -DskipTests'
            }
        }
       stage('build image')
        {
            steps{
                sh 'docker build -t dockerjenkins:1.01 .'
            }
        } 
        stage('pushing to dockerhub')
        {
            steps{
                sh 'docker tag dockerjenkins:1.01 chethanmk666/dockerjenkins:1.01 '
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'

                sh 'docker push chethanmk666/dockerjenkins:1.01 '
            }
        }
       
         //stage('Deploy App') {
      //steps {
           
        //kubernetesDeploy configs: '**/appDeployment.yaml', kubeConfig: [path: ''], kubeconfigId: 'kube', secretName: '', ssh: [sshCredentialsId: '*', sshServer: ''], textCredentials: [certificateAuthorityData: '', clientCertificateData: '', clientKeyData: '', serverUrl: 'https://']

          //   }
        //}
        
    }
}




