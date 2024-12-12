pipeline {
    agent { 
        node {
            label 'docker-agent-python'
            }
      }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                # Create a virtual environment
                python3 -m venv venv
                # Activate the virtual environment
                . venv/bin/activate
                # Install dependencies
                pip install -r myapp/requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                # Activate the virtual environment
                . venv/bin/activate
                # Change to the 'myapp' directory
                cd myapp
                # Run the Python script with no arguments
                python3 hello.py
                # Run the Python script with the argument --name=Yacquub
                python3 hello.py --name=Yacquub
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
} 