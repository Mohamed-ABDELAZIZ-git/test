pipeline{
    agent any
    stages{
        stage('APP') {
            steps{
                //sh 'nc  0.0.0.0 5000 < /dev/null ; echo $?'
                echo 'Run the app'
                sh 'python3 app.py &'
                sh "sleep 10"
                sh 'nc  0.0.0.0 5000 < /dev/null ; echo $?'
            }
        }
        stage('TEST') {
            steps{
                //waitUntil {sh 'nc -vz 0.0.0.0 5000'==1}
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
