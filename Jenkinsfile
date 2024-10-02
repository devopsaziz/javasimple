pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-11-openjdk'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout code from the 'main' branch
                git branch: 'main', url: 'https://github.com/devopsaziz/javasimple.git'
            }
        }

        stage('Compile Java Program') {
            steps {
                // Compile the Java program
                script {
                    if (isUnix()) {
                        sh 'javac HelloWorld.java'
                    } else {
                        bat 'javac HelloWorld.java'
                    }
                }
            }
        }

        stage('Run Java Program') {
            steps {
                // Run the compiled Java program
                script {
                    if (isUnix()) {
                        sh 'java HelloWorld'
                    } else {
                        bat 'java HelloWorld'
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
    }
}
