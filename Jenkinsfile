pipeline {
    agent any

    tools {NodeJS "node"}

    stages {

        stage('Git'){
            steps {
                git 'https://github.com/aatharvauti/react-sandbox'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install project dependencies
                    sh 'npm install'
                    // Build your React app
                    sh 'npm run build'
                }
            }
        }

        stage('Build and Run') {
            steps {
                script {
                    try {

                        // Run the app
                        sh 'npm run start'

                        // If everything works, echo "Good to go!"
                        echo 'Good to go!'
                    } catch (Exception e) {

                        // If there's an error, echo "error"
                        echo 'error'
                        currentBuild.result = 'FAILURE'
                    }
                }
            }
        }
    }
}
