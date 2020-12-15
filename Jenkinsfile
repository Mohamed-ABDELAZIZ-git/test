pipeline{
    agent any
    stages{
        stage('APP') {
            steps{
                echo 'Run the app'
                waitUntil {
                    test = sh 'nc -vz 0.0.0.0 5000';
                    return test == 0;
                }
                sh 'python3 app.py &'
              //  sh "sleep 10"  
            }
        }
        stage('TEST') {
            steps{
                //waitUntil {sh 'nc -vz 0.0.0.0 5000'}
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
