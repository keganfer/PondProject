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
	    /*
        stage('Dock push') {
            steps {
                sh 'docker build -t lutokepondproject .'
	    sh 'docker tag lutokepondproject:latest keganferreira/lutokepondproject:latest'
		withDockerRegistry([ credentialsId: 'DockerCreds', url: '' ]) {
	    sh 'docker push keganferreira/lutokepondproject'
		}
            }
        }
	*/
        stage('Execute') {
            steps {
                echo 'executing'
    		sh 'docker-compose up -d'

            }
        }

    }
}
