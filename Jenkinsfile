pipeline{
    agent any 
    stages{
        stage('clone-jenkins'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkinsgit', url: 'https://github.com/YomiPounds/branches-pipelines.git']]])
            }
        }
        stage('main-parallel-job'){
            parallel{
                stage('sub-parallel-job'){
                    steps{
                        sh 'chmod +x yomi.sh'
                        sh 'bash -x yomi.sh'
                    }
                }
                stage('2-sub-parallel-job'){
                    steps{
                        sh 'free -m'
                    }
                }
            }
        }
        stage('main-job'){
            steps{
                echo "My name is Abayomi and I am a Devops Engineer"
            }
        }
        stage('3-main-job'){
            when{
                branch "uat"
            }
            steps{
                sh 'whoami'
            }
        }
    }
}
