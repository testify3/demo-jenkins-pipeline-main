pipeline {
    agent {
        docker {
            image 'maven:3.8.4-jdk-11'
            args '-v /root/.m2:/root/.m2' // Optional: cache Maven dependencies
        }
    }

    stages {
        stage('Compiler le code') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Exécuter les tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Publier les résultats de tests') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }
    }

    post {
        success {
            echo 'Le pipeline a réussi !'
        }
        failure {
            echo 'Le pipeline a échoué.'
        }
    }
}
