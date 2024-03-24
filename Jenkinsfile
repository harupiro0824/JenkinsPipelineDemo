pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from githu hook trigger'
            }
        }
        stage('Build') {
            steps {
                echo 'Building'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp [ec2-user@ip-172-31-34-33 TestJob]$ ced /var/lib/jenkins/workspace/JenkinsPipeline/index.html S3://test-env-henkins-moriya/')
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing'
            }
        }
    }
}
