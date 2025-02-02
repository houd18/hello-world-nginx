pipeline {
    agent any

    environment {
        GIT_REPO = "https://github.com/houd18/hello-world-nginx.git"
        WEB_ROOT = "/var/www/html"  // Path where Nginx serves files
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: env.GIT_REPO
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    sh """
                        sudo mv index.html ${WEB_ROOT}/index.html
                        sudo systemctl restart nginx
                    """
                }
            }
        }
    }
}
