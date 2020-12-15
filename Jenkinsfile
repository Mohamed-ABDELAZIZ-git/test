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
                waitUntil { 
     script { 
     def r = sh script: 'wget -q http://0.0.0.0:5000/ -O /dev/null', returnStatus: true 
     return (r == 0); 
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
