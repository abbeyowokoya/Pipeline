pipeline {
    agent any
        stages{
            stage ('Download package from S3') {
                steps{
                      sh '''
                          echo 'exporting AWS Environment'
                          export DEPLOYMENT_ENVIRONMENT=Dev
                          printenv
                          aws s3 ls
                         aws s3 cp s3://mdm-npss/dev/apache-tomcat-9.0.46.tar.gz /home/ec2-user/
                       '''
            }       
        }
            //stage('Deploy'){       
                //sshPublisher(publishers: [sshPublisherDesc(configName: 'SERVER_NAME', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'apt-get update', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
               //}

            stage('Install Package'){
                steps{
                    //withCredentials([string(credentialsId: '', variable: '')]) {
                        sh '''
                            sudo cd /opt
                            sudo tar -xvf apache-tomcat-9.0.46.tar.gz
                            sudo cd apache-tomcat-9.0.46/bin
                            ./startup.sh
                          
                        '''
                    //}
                }
           }

        }      
            
}
