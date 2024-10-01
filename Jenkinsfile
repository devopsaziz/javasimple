pipeline {
    agent any

    environment {
        JAVA_HOME = tool 'JDK11'  // Assuming JDK 11 is configured in Jenkins Global Tool Configuration
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Clone the repository from GitHub
                git 'https://github.com/devopsaziz/javasimple.git'
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
            // Cleanup if necessary
            echo 'Pipeline complete.'
        }
    }
}
