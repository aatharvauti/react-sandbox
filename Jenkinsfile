pipeline {
    agent any

    environment {
        NODE_VERSION = '18.17.1'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Use the specified Node version
                    // def nodeTool = tool name: "NodeJS ${NODE_VERSION}", type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    // env.PATH = "${nodeTool}/bin:${env.PATH}"

                    // Install project dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Build and Run') {
            steps {
                script {
                    try {
                        // Build your React app
                        sh 'npm run build'

                        // Run the app
                        sh 'npm start'

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
