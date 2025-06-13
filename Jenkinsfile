pipeline {
    agent any

    stages {
        stage('Pull data form git') {
            steps {
                git branch: 'main', url: 'https://github.com/Jayeshk15/jayesh-flask.git'
            }
        }
        
        stage('Build Image') {
            steps {
                sh 'ls -l'
                sh 'docker build -t Jayeshk15/myweb .'
            }
        }
        
        stage('push image') {
            steps {
                sh 'docker push Jayeshk15/myweb'
            }
        }

        stage('remove existing service') {
            steps {
                sh 'docker service rm myservice'
            }
        }
        
	stage('creat service') {
            steps {
                sh 'docker service create --name myservice -p 4000:4000 --replicas 2 Jayeshk15/myweb'
            }
        }
    }
}
