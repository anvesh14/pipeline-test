properties = null
def workspace = '/root/pipeline-test'
def loadProperties() {
    node {
        checkout scm
        properties = readProperties file: "${Env}.properties"
        echo "Immediate one ${properties.repo}"
    }
}

pipeline {
    agent none

    stages {           
        stage ('prepare') {
            agent any

            steps {
                dir("${params.workspace}"){
                script {
                    loadProperties()
                    echo "Later one ${properties.ansible}"
                }
            }
                
            }
            
        }
        stage('Build') {

            agent any

            steps {
                echo properties.branch
            }

        }
    }
}
