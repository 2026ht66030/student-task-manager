pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('checkout') {
            steps {
                echo 'checking out source code'
                checkout scm
            }
        }
        stage('build') {
            steps {
                echo 'installing python dependencies'
                sh ''' 

                    python3 -m venv .venv 

                    .venv/bin/pip install -r requirements.txt 

                ''' 
            }

        }
        stage('test') {
            steps {
                echo 'Running python test'
                sh ''' 

                    .venv/bin/python3 -m pytest 

                ''' 
            }
        }
    }
}