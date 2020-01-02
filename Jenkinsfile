
pipeline {
    agent { docker { image 'python:3.5.1' } }
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
                unestable {
                    echo 'This will run if the run was marked as unestable'
                }
                changed {
                    echo 'This will run if the state of the Pipeline has changed'
                    echo 'For example, if the Pipeline has been failed and is now successful'
                }
            }
}


