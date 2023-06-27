pipeline{
    agent any
    stages{
        stage('Git-Checkout'){
            steps{
                echo "Checking out from git repo";
                git branch: 'main', url: 'https://github.com/OmarySudi/scripted_pipeline.git'
            }
        }
        stage('Build'){
            steps{
                echo "Building the checkout project";
                bat 'Build.bat';
            }
        }
        stage('Unit-test'){
            steps{
                echo "Running unite tests";
                bat 'Unit.bat'
            }
        }
        
        stage('Quality-Gate'){
            steps{
                echo "Verifying Quality Gates";
                bat 'Quality.bat'
            }
        }
        
               
        stage('Deploy'){
            steps{
                echo "Deploying to stage environment for more tests";
                bat 'Deploy.bat'
            }
        }
    }

    post{
        always{
            echo "This will always run"
        }

        success{
            echo "This will run only if successfully"
        }

        failure{
            echo "This will run only if failed"
        }

        unstable{
            echo "This will run only if the run is marked as unstable"
        }

        changed{
            echo "This will run only if state of pipeline has changed"
        }
    }
}
