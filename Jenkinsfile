pipeline { 
    agent any 
    stages {
        stage('Git Clone') {
            steps {
                echo "checking out the repo from git"
                git clone 'https://github.com/ashishcsjm/devOps_projCert.git'
            
            }
        }
        stage('Docker build and deploy container'){
            steps { 
                script {
                    build job: 'docker_deployment' , parameters: [
                        [$class: 'StringParameterValue', name: 'PARAM_PARENT_BUILD', value: ${BUILD_NUMBER}]
                        ]
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
