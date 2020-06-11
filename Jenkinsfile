pipeline {
    agent any

    stages {
        stage ('Initialize') {
            steps {
                echo 'Cleaning the target directory/build area'
                sh 'mvn clean -f "backend"'
            }
        }
        stage ('Validate') {
            steps {
                echo 'Validating the project & dependencies are downloaded.'
            }
        }
        stage('Compile') {
            steps {
                echo 'Compiling Source code ...'
                sh 'mvn clean compile -f "backend"'
            }
        }

        stage('Test') {
            steps {
                echo 'Running all tests.'
                sh 'mvn test -f "backend"'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging'
                sh 'mvn package -B -T 2.0C -DskipTests -f "backend"'
            }
        }


        stage('Execute') {
            steps {
                echo 'executing'
                script {
                    sh 'docker-compose up -d'
                }

            }
        }

    }
}
