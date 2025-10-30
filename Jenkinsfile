pipeline {
    agent {
        docker { image 'maven:3.8.4-jdk-11' } // Utilisation de l'image Docker Maven avec JDK 11
    }
    
    environment {
        MVN_HOME = '/usr/share/maven' // Spécification du chemin Maven
    }

stage('Cloner le dépôt') {
    steps {
        git branch: 'main', url: 'https://github.com/testify3/demo-jenkins-pipeline-main.git'
    }
}


        stage('Compiler le code') {
            steps {
                script {
                    sh 'mvn clean install'  // Compilation du projet
                }
            }
        }

        stage('Exécuter les tests') {
            steps {
                script {
                    sh 'mvn test'  // Lancement des tests
                }
            }
        }

        stage('Publier les résultats de tests') {
            steps {
                junit '**/target/test-*.xml'  // Publication des résultats des tests
            }
        }
    }

    post {
        success {
            echo 'Le pipeline a réussi !'
        }
        failure {
            echo 'Le pipeline a échoué !'
        }
    }
}
