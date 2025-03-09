pipeline {

    agent any
    stages {

        stage('build') {

            steps {

                sh 'mvn -B -DskipTests clean package'

            }
        }

        stage('Test') {
            steps{
                sh 'mvn test'
            }
            post {

                always{
                    junit 'target/surefire-reports/*.xml'
                    // it find the result from surefire ports, if any test has failed then build will also fail
                }

            }
        }

        stage('deliver') {
            steps {
                steps {

                   sh './jenkins/scripts/deliver.sh'
                }

            }
        }

    }

}