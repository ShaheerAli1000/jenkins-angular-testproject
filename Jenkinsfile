pipeline {
    agent any

        stage('Install Dependencies') {
            steps {
                // Install npm dependencies
                sh 'npm install'
            }
        }

        stage('Lint') {
            steps {
                // Run linting to check for code style issues
                sh 'npm run lint'
            }
        }

        stage('Build') {
            steps {
                // Build the Angular project
                sh 'npm run build --prod'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                sh 'npm run test -- --watch=false --browsers=ChromeHeadless'
            }
        }

        stage('Post-build Cleanup') {
            steps {
                // Optionally, clean up temporary files (e.g., dist folder)
                sh 'rm -rf dist'
            }
        }
    }

    post {
        // Send notifications or perform actions based on the build status
        success {
            echo 'Build completed successfully.'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
