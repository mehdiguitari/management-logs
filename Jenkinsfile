pipeline {
    environment {
        registry = "localhost:5000"
        }
    agent {
        node {
            label 'pfe-machine'
        }
    }  
    stages {
        stage('Cloning Git') {
            agent {
                label 'pfe-machine'
            }
           steps {
                sh "mkdir -p ${deployjobname}"
                dir("${deployjobname}")
                {
                    git branch: 'master',
                       url: '${sourceCodeUrl}'
                       // credentialsId: 'github-auth'
                }
            }
        }
        stage('Building image') {
            agent {
                label 'pfe-machine'
            }
        }   
        stage('Deploy image') {
            agent {
                label 'pfe-machine'
            }
           steps {
                dir("${deployjobname}")
                {
                script {
                        sh "docker-compose up --force-recreate -d"
                }
                }
            }
        }
        stage('Testing') {
            agent {
                label 'pfe-machine'
            }
           steps {
                dir("${deployjobname}")
                {
                script {
                        sh "docker ps | grep $deployjobname"
                }
                }
            }
        }
    }      
}
