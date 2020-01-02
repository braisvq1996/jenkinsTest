
pipeline {
    agent { 
        docker { 
            image 'python:3.5.1' 
                } 
          }
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE = 'splite'
    }
    stages {
        stage('build') {
            steps {
                timeout(time: 3, unit: 'MINUTES') {
                    retry(5) {
                        sh 'python --version'
                        sh 'echo "Hello World"'
                        sh '''
                            echo "Multiline shell steps works too"
                            ls -lah
                        '''
                        sh 'echo "Database engine is ${DB_ENGINE}"'
                        sh 'echo "DISABLE_AUTH is ${DISABLE_AUTH}"'
                        sh 'printenv'
                    }
                }
            }
        }
    }
            post {
                always {
                    echo 'This will always run'
                }
                success {
                    echo 'This will run if successful'
                }
                failure {
                    echo 'This will run if failed'
                }
                unstable {
                    echo 'This will run if the run was marked as unestable'
                }
                changed {
                    echo 'This will run if the state of the Pipeline has changed'
                    echo 'For example, if the Pipeline has been failed and is now successful'
                }
            }
}


