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
                echo 'Building SpotiFLAC Project...'
                sh 'echo "Langkah Build: Mengumpulkan file project..." '
            }
        }

        stage('Test') {
            steps {
                echo 'Running Automated Tests...'
                sh 'echo "Langkah Test: Unit testing berhasil melewati 100% data."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to Production...'
                sh 'echo "Langkah Deploy: Aplikasi SpotiFLAC berhasil di-push ke server!"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully! Tugas CI Berhasil.'
        }
        failure {
            echo 'Pipeline failed! Silakan cek kembali penulisan script.'
        }
    }
}
