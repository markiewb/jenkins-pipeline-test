pipeline {
    agent any
    //agent { docker { image 'maven:3.3.3' } }
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 
'How should I greet the world?')
    }

    stages {
        stage('Example') {
            steps {
                echo "${params.Greeting} World!"
            }
        }    
        stage('Build') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                sh 'date'
                echo currentBuild.displayName
                echo env.BUILD_ID
            }
        }
        stage('Test') {
            steps {
                sh 'date'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 
'SUCCESS' 
              }
            }
            steps {
                echo 'SUCCESSFUL'
            }
        }

    }
    post {
        always {
            echo 'always'
        }
        failure {
            echo 'failure'
        }
    }
    
}
