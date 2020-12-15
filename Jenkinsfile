pipeline{
    agent any
    stages{
        stage('APP') {
            steps{
                echo 'Run the app'
                sh 'python3 app.py &'
            }
        }
        stage('TEST') {
            options {
                timeout(time: 10, unit: 'SECONDS') {
                    echo 'Loading...'
                }
            }
            steps{
                echo 'Test the app'
                sh 'python3 Integration_test.py'
            }
        }
        stage('STOP') {
            steps{
                echo 'Exit the app'
                sh 'kill -INT $(lsof -t -i :5000)'
            }
        }
    }
}
