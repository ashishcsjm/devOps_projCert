pipeline {
    agent any 
    stages {
        stage('Git Clone') {
            steps {
                echo "checking out the repo from git"
                git 'https://github.com/ashishcsjm/devOps_projCert.git'
            
            }
        }
        stage('Docker build'){
            steps {
                echo "building Docker Image"
                docker build -t ashishag2511/website:image$BUILD_NUMBER /var/lib/jenkins/workspace/devops_projCert
            }
        }
        
        stage('Deployment-Running Docker Container') {
            steps {
                script {
                    echo "deployment"
                    docker run -it -d -p 9091:80 ashishag2511/website:image$BUILD_NUMBER
                }
            }
        }
     //   stage('publish html report') {
       //     steps{
         //       echo "publishing the html report"
           //     publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
//            }
  //      }
        stage('clean up') {
            steps {
                echo "cleaning up the workspace"
                cleanWs()
            }
        }
        
    }
}
