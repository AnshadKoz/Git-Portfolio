pipeline{
    agent none
    stages{
        stage('Build'){
            agent {
                label 'build'
            }
            steps{
                deleteDir()
                sh '''
                   git clone https://github.com/AnshadKoz/Git-Portfolio.git
                   ls -la
                   '''
                   stash name:'webpage', includes:'Git-Portfolio/**'
            }
        }
        stage ('Deploy'){
            agent{
                label 'deploy'
            }
            
            steps{
                deleteDir()
                unstash 'webpage'
                
                sh '''
                   sudo rm -rf /var/www/html/*
                   sudo cp -r Git-Portfolio/* /var/www/html/
                   ls -la /var/www/html/
                   '''
            }
        }
    }
}
