pipeline {
    agent {
        node {
                label 'gwtest'
        }
    }
    stages {
        stage('check_confilt') {
            steps {
                echo 'enter into confilt check'
                java -version
                pwd
            }
        }
        stage('prepare_env') {
            steps {
                echo 'enter into prepare env'
            }
        }
        stage('run_test') {
            steps {
                echo 'enter into test stage'
                robot --version
                python --version
            }
        }
    }
}
