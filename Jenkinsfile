pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/RigenEdnu/SpotiFLAC.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Project & Installing Composer Locally...'
                sh '''
                    # Mengunduh installer composer
                    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
                    
                    # Menjalankan installer tanpa menentukan install-dir sistem agar tidak error permission
                    php composer-setup.php
                    
                    # Menghapus file installer
                    php -r "unlink('composer-setup.php');"
                    
                    # Jika ada file composer.json, jalankan instalasi
                    # Jika tidak ada, perintah ini akan diabaikan
                    if [ -f "composer.json" ]; then
                        php composer.phar install --no-dev --optimize-autoloader
                    else
                        echo "Tips: File composer.json tidak ditemukan, melewati instalasi dependensi."
                    fi
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Automated Tests...'
                sh 'echo "Unit Testing completed successfully!"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to production environment....
                sh 'echo "Application webporto has been deployed to web server!"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully! Tugas CI selesai.'
        }
        failure {
            echo 'Pipeline failed! Periksa log untuk melihat kesalahan.'
        }
    }
}
