pipeline {
    agent any

    environment {
        GIT_REPO = "https://github.com/houd18/hello-world-nginx.git"
        WEB_ROOT = "/var/www/html"
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
                        sudo -S mkdir -p ${WEB_ROOT}
                        sudo -S cp index.html ${WEB_ROOT}/index.html
                        sudo -S chmod 644 ${WEB_ROOT}/index.html
                        sudo -S chown www-data:www-data ${WEB_ROOT}/index.html
                        sudo -S systemctl restart nginx
                    """
                    
                }
            }
        }
    }
}
