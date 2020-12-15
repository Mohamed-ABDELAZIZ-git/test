pipeline{
    agent any
    stages{
        stage('RUN') {
            steps{
                echo 'Run the app'
                sh 'python3 app.py'
            }
        }
        stage('RUN2') {
            stage('TEST') {
                steps{
                    echo 'Test the app'
                    sh 'python3 Integration_test.py'
                }
            }
            stage('STOP') {
                steps{
                    echo 'Exit the app'
                    sh 'killall'
                }
            }
        }
    }
}
