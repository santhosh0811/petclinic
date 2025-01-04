@Library('my-shared-library@main') _

pipeline {
    agent { label 'dev1' }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        MAVEN_HOME = '/usr/share/maven'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    pipeline1.check_out()
                }
            }
        }

        stage('Set up Java') {
            steps {
                script {
                    pipeline1.setup_java()
                }
            }
        }

        stage('Set up Maven') {
            steps {
                script {
                    pipeline1.setup_maven()
                }
            }
        }

        stage('Build with Maven') {
            steps {
                script {
                    pipeline1.setup_clean()
                }
            }
        }

        stage('Upload Artifact') {
            steps {
                script {
                    pipeline1.upload_artifact('target/*.jar')
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    pipeline1.run_application()
                }
            }
        }

        stage('Validate App is Running') {
            steps {
                script {
                    pipeline1.validate_app()
                }
            }
        }

        stage('Keeping Application Up for 2 Minutes') {
            steps {
                script {
                    pipeline1.sleep_app()
                }
            }
        }

        stage('Gracefully Stop Spring Boot App') {
            steps {
                script {
                    pipeline1.stop_app()
                }
            }
        }
    }

    post {
        always {
            script {
                echo 'Cleaning up resources...'
                // Add any cleanup steps if required
            }
        }
    }
}
