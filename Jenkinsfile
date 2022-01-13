pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Testing..'
                sh './mvnw test'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh './mvnw package'
            }
        }
        stage('Push to registry') {
            steps {
                echo 'Pushing..'
            }
        }
        stage('Deploy') {
            when {
                branch 'main'  //only run these steps on the main branch
            }
            steps {
                echo 'Deploying....'
                sh 'docker run -d -p 8083:8080 petclinic:latest'
            }
        }        
    }
}