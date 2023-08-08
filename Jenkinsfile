pipeline {
    environment {
        registry = "localhost:5000"
        deployjobname = "log_management"
        sourceCodeUrl = "https://github.com/mehdiguitari/management-logs.git"
        }
    agent {
        node {
            label 'maître'
        }
    }  
    stages {
        stage('Cloning Git') {
            agent {
                label 'maître'
            }
           steps {
                sh "mkdir -p ${deployjobname}"
                dir("${deployjobname}")
                {
                    git branch: 'main',
                       url: '${sourceCodeUrl}'
                       // credentialsId: 'github-auth'
                }
            }
        }
        stage('Building image') {
            agent {
                label 'maître'
            }
        }   
        stage('Deploy image') {
            agent {
                label 'maître'
            }
           steps {
                dir("${deployjobname}")
                {
                script {
                        sh "kubectl apply -f deployement.yaml"
                }
                }
            }
        }
        stage('Testing') {
            agent {
                label 'maître'
            }
           steps {
                dir("${deployjobname}")
                {
                script {
                        sh "kubectl get pods -A"
                }
                }
            }
        }
    }      
}
