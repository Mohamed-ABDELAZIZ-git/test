pipeline{
    agent any
    stages{
        stage('APP') {
            steps{
                echo 'Run the app'
                sh 'python3 app.py &'
              //  sh "sleep 10"  
            }
        }
        stage('TEST') {
            steps{
                waitUntil {
                    //sh 'nc -vz 0.0.0.0 5000'==1}
                
                
       script {
         def r = sh script: 'nc -vz 0.0.0.0 5000', returnStdout: true
         return (r == 0);
       }
                
                }
                
                
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
